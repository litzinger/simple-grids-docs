---
title: Template Tags
taxonomy:
    category: docs
---

### Variables

The following variables are available in both Simple Table and Simple Grid tag pairs.

    {row_id}
    {total_rows}
    {count}
    {index}
    {is_first_row}
    {is_last_row}
    {switch="a|b"}

### Parameters

    prefix=""
    backspace=""

### Example template code

#### Simple Table (standalone)

Note you can optionally prefix all of Simple Grid and Simple Table field variables with the ``prefix=""`` parameter.

Since Simple Table does not have named columns, all of the column values are available with the ``{value}`` variable.

    <table>
    {simple_table_field prefix="st:"}
        <tr data-id="{st:row_id}" switch="{switch='odd|even'}">
            {st:columns}
                {if st:is_first_row}
                    <th data-id="{st:column_id}">
                        {st:value}
                    </th>
                {if:elseif st:is_last_row}
                    <td data-id="{st:column_id}">
                        <i>{st:value}</i>
                    </td>
                {if:else}
                    <td data-id="{st:column_id}">
                        {st:value}
                    </td>
                {/if}
            {/st:columns}
        </tr>
    {/simple_table_field}
    </table>

#### Simple Table (inside Grid)

    {grid_field}
        <table>
        {grid_field:simple_table_field}
            <tr switch="{switch='odd|even'}">
                {columns}
                    {if is_first_row}
                        <th data-id="{column_id}">
                            {value}
                        </th>
                    {if:elseif is_last_row}
                        <td data-id="{column_id}">
                            <i>{value}</i>
                        </td>
                    {if:else}
                        <td data-id="{column_id}">
                            {value}
                        </td>
                    {/if}
                {/columns}
            </tr>
        {/grid_field:simple_table_field}
        </table>
    {/grid_field}
    
#### Simple Table (inside Bloqs)

    {bloqs_field}
        {block}
            {simple_table_field}
                <tr switch="{switch='odd|even'}">
                    {columns}
                        {if is_first_row}
                            <th data-id="{column_id}">
                                {value}
                            </th>
                        {if:elseif is_last_row}
                            <td data-id="{column_id}">
                                <i>{value}</i>
                            </td>
                        {if:else}
                            <td data-id="{column_id}">
                                {value}
                            </td>
                        {/if}
                    {/columns}
                </tr>
            {/simple_table_field}
        {/block}
    {/bloqs_field}

#### Simple Grid (inside Grid)

Unlike Simple Table, Simple Grid does have named columns. In this case the column names are ``{description}`` and ``{file}``.
Simple Grid operates very similarly to the native Grid field, but does not have varible modifiers such as ``:sum`` or ``:average``.

    {grid_field}
        {grid_field:total_rows}
        <table>
        {grid_field:simple_grid_field}
            <tr switch="{switch='odd|even'}" data-total-rows="{total_rows}">
                <th>{description}</th> <!-- This is a column name in the Simple Grid field -->
                <td>{file}</td> <!-- This is a column name in the Simple Grid field -->
            </tr>
        {/grid_field:simple_grid_field}
        </table>
    {/grid_field}
