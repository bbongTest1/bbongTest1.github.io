{%- assign dirMapping = site.data.history_dir_mapping -%}
{%- for dir in dirMapping -%}
    {{- dir.start_path -}}
    {%- assign dirPath = dir.additional_mapping_path -%}
    {{- dirPath -}}
{%- endfor -%}

{%- if site.useVersionTree -%}
    <div id="version_tree_list">
        {%- assign validVerInfo = site.data.product_version.version_info_list -%}
        {%- for verInfo in validVerInfo -%}
            {%- assign curId = "version_tree_" | append: verInfo | replace: " ", "_" | downcase -%}
            <span id="{{ curId }}">
                {%- include liquid_searchVersionTreeFile.html ver=verInfo curPath="" targetRelativePath="sidelist-full-tree.html" -%}
            </span>
        {%- endfor -%}
        <span id="complete_loading_tree"></span>
    </div>
{%- endif -%}
