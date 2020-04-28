---
title: 如何读取不同来源的图像
description: 本文介绍DBR如何读取不同来源的图像，包括文件读取、内存读取和视频流读取
keywords: file memory video stream
---
# 如何读取不同来源的图像
DBR算法提供多种方式对不同来源的图像进行读取，本文会对以下这些方式进行介绍。
1. [文件读取](#文件读取)
2. [内存读取](#内存读取)
3. [视频流读取](#视频流读取)
## 文件读取
对于图片文件，DBR提供以下两种接口读取处理。
* [DecodeFile]()
* [DecodeFileInMemory]()

以下是两个接口的示例代码
``` c++
//DecodeFile示例
CBarcodeReader* reader = new CBarcodeReader();
reader->InitLicense("填入你的license");
int errorCode = reader->DecodeFile("图片路径", "");
delete reader;
```
```c++
//DecodeFileInMemory示例
CBarcodeReader* reader = new CBarcodeReader();
reader->InitLicense("填入你的license");
unsigned char* pFileBytes;
int nFileSize = 0;
GetFileStream("图片路径", &pFileBytes, &nFileSize); //读取文件至内存
int errorCode = reader->DecodeFileInMemory(pFileBytes, nFileSize, "");
delete reader;
```
## 内存读取
对于内存中的图像数据，DBR提供以下接口进行读取处理。
- [DecodeBuffer]()   
对于内存中的图像像素数据，可以通过该接口来读取。多用于视频流数据中，用户获取一帧的图像数据后，调用该接口解码。主要参数如下
   - pBufferBytes   
   图像像素数据的指针。
   - iWidth   
   图像像素数据的宽度。
   - iHeight   
   图像像素数据的高度。
   - iStride   
   图像像素数据单行 Byte 数量。
   - format   
   图像单个像素的数据格式，与图像depth相对应。详细枚举参考 [ImagePixelFormat]()
   
   下面使用一个实际的例子来说明这几个参数。下图是一个 152 * 152 的QR图片，图像有RGB三个通道，图像 depth = 24bit (即每一个像素占内存空间24bit) ，因而在此例子中 format 取值是 [IPF_RGB888]()    
   图像宽度 iwidth = 152px，那么图像一行所占内存大小的 bit 数量是 iwidth * depth，在此例子中就是 3648 bit   
   如果现在我们利用 `int ( 32 bit / int )` 类型的数组存储图像的像素数据，那么一行图像像素数据需要的 `int` 数组长度是 （iwidth * depth + 31） / 32 , 那么实际的图像像素数据的单行 byte 数量 iStride 的计算就是   
   `
   iStride =（iwidth * depth + 31） / 32 * 4   
   `   
   那么图像的像素数据 pBufferBytes 的构造就是    
   `
   int* pBufferBytes = new int[(width * depth + 31) / 32 * iHeight];
`   
构造完成 pBufferBytes 之后就是读取图像数据填入即可。

   ![alt dbr_qr][1]   
   下面是一个示例程序,在这个例子中我们利用opencv进行图像数据读取，并调用 DecodeBuffer 接口   

``` cpp
#include "DynamsoftBarcodeReader.h"
#include <opencv2/opencv.hpp>
using namespace cv;
using namespace std;
#ifdef _WIN64
#pragma comment(lib, "DBRx64.lib")
#else
#pragma comment(lib, "DBRx86.lib")
#endif

int main()
{
	int ret = 0;
	CBarcodeReader* reader = new CBarcodeReader();
	reader->InitLicense("your license here");
	Mat image = cv::imread("your img file path");
	if (image.type() == CV_8UC3) {
		ret = reader->DecodeBuffer(image.data, image.cols, image.rows, image.cols * 3, IPF_RGB_888);
	}
	else if (image.type() == CV_8UC1) {
		ret = reader->DecodeBuffer(image.data, image.cols, image.rows, image.cols, IPF_GRAYSCALED);
	}
	TextResultArray* pResults = NULL;
	reader->GetAllTextResults(&pResults);
	delete(reader);
	return 0;
}
```

- [DecodeBase64String]()   
对于Base64编码的图像数据使用该接口进行读取解码。
- [DecodeDIB]()   
对于DIB格式的图像数据使用该接口进行读取解码。

## 视频流读取
DBR提供针对视频流的若干处理接口，方便用户处理视频帧队列和多线程等问题。   
DBR会创建一个待处理队列来存储当前要处理的视频帧，并创建一个解码线程来处理该队列。解码线程每次取队列中最新的一帧来处理，解码完成后将其移出队列，进行下一次的处理，解出的结果会放入一个结果队列中。如果待处理队列的长度达到了设定的最大值，解码线程会尽快退出当前的处理帧，并清空待处理队列，等待新的帧加入队列重新开始处理，以防止某一帧出现耗时太久的问题。   
DBR也提供模糊帧的过滤功能，开启后，DBR会计算待处理队列中图像帧的清晰度，清晰度低于设定阈值的帧会从待处理队列中移除。  
高级用户若有特殊需求也可以绕开这些接口，自行处理相应问题。主要接口如下   
- [AppendFrame]()   
将当前帧加入到待处理队列
- [StartFrameDecoding]()  
开启解码线程进行解码处理
- [StartFrameDecodingEx]()   
开启解码线程进行解码处理,相比于 [StartFrameDecoding]()，该接口可通过传入参数 [FrameDecodingParameters]() 对象对DBR处理视频流时涉及的配置进行修改
- [SetTextResultCallback]()   
设置解码完成时的回调函数。DBR在处理视频流时会开启一个线程循环检查结果队列，如有新的结果放入队列，则会调用该回调函数
- [StopFrameDecoding]()   
停止并退出解码线程
- [InitFrameDecodingParameters (FrameDecodingParameters *pParameters) ]()   
初始化 [FrameDecodingParameters]() 对象
- [FrameDecodingParameters]()   
该结构体提供了一系列的配置参数供用户配置DBR涉及视频流的处理方式。主要字段如下
    - [maxQueueLength]()   
    设定待处理队列的最大长度
    - [maxResultQueueLength]()  
    设定结果队列的最大长度
    - [width]()  
    图像的宽度
    - [height]()   
    图像的高度
    - [stride]()   
    图像单行的Byte数量
    - [imagePixelFormat]()   
    图像单个像素的格式
    - [region]()   
    设定DBR算法要处理的区域。这是一个矩形区域，如果设置后，DBR仅在该区域范围内做定位解码处理
    - [autoFilter]()   
是否要开启模糊帧过滤。默认1，开启模糊帧的过滤
    - [threshold]()   
    进行模糊帧过滤时的过滤阈值。范围0-1，数值越小，图像帧越容易被过滤掉
    - [fps]()   
    视频流帧率，DBR在进行模糊帧过滤逻辑时会参考这个值。如果没有设置，那么DBR会根据调用 [AppendFrame]() 的频率来进行估算

    下面使用一个实际的例子来演示这些接口。在这个示例中，我们利用 opencv 读取摄像头数据，并调用 DBR 的视频流接口来解码。

```c++
#include <opencv2/core.hpp>
#include <opencv2/videoio.hpp>
#include <opencv2/highgui.hpp>
#include <iostream>
#include <vector>
#include "Include/DynamsoftBarcodeReader.h"
using namespace cv;
using namespace std;
using std::cerr; 
using std::endl;
using std::cin;

#ifdef _WIN64
#pragma comment(lib, "Lib/DBRx64.lib")
#else
#pragma comment(lib, "Lib/DBRx86.lib")
#endif

//解码完成时的回调函数
void textResultcallback(int frameId, TextResultArray *pResults, void * pUser)
{
	for (int iIndex = 0; iIndex < pResults->resultsCount; iIndex++)
	{
		printf("Barcode %d, Value %s\n", iIndex + 1, pResults->results[iIndex]->barcodeText);
	}

	CBarcodeReader::FreeTextResults(&pResults);
}

//解码出现错误时的回调函数
void errorcb(int frameId, int errorCode, void * pUser)
{
	printf("frame = %d errorcode = %d, %s\n", frameId, errorCode, CBarcodeReader::GetErrorString(errorCode));
}

int main()
{
   Mat frame;
   cout << "Opening camera..." << endl;
   VideoCapture capture(0); // open the first camera
   if (!capture.isOpened())
   {
      cerr << "ERROR: Can't initialize camera capture" << endl;
      return 1;
   }
	 
   int iRet = -1;
   CBarcodeReader reader;
   iRet = reader.InitLicense("输入你的license");
   if (iRet != 0)
   {
      printf("%s\n", CBarcodeReader::GetErrorString(iRet));
      return -1;
   }
   reader.InitRuntimeSettingsWithString("输入你的模板路径", CM_OVERWRITE);	
   reader.SetTextResultCallback(textResultcallback, NULL); // 设置解码完成时的回调
   reader.SetErrorCallback(errorcb, NULL); // 设置出现错误时的回调
   FrameDecodingParameters parameters;
   reader.InitFrameDecodingParameters(&parameters);

   capture >> frame;
   parameters.width = capture.get(CAP_PROP_FRAME_WIDTH);
   parameters.height = capture.get(CAP_PROP_FRAME_HEIGHT);
   parameters.maxQueueLength = 30;
   parameters.maxResultQueueLength = 30;
   parameters.stride = frame.step.p[0];
   parameters.imagePixelFormat = IPF_RGB_888;
   iRet = reader.StartFrameDecodingEx(parameters, "");
   if (iRet != 0)
   {
      printf("%s\n", CBarcodeReader::GetErrorString(iRet));
      return -1;
   }
   for(;;)
   {
      capture >> frame; // read the next frame from camera
      if (frame.empty())
      {
         cerr << "ERROR: Can't grab camera frame." << endl;
         break;
      }
      reader.AppendFrame(frame.data);
      imshow("Frame", frame);
      int key = waitKey(1);
      if (key == 27/*ESC*/)
         break;
   }
   reader.StopFrameDecoding();
   return 0;
}
```

[1]: assets/read-from-diff-source/dbr_qr.png


