---
title: "Add interactive sort to a table or matrix in paginated reports"
description: Enable users to change the sort order of rows and columns in tables and matrices in paginated reports using interactive sort buttons in Report Builder.
author: maggiesMSFT
ms.author: maggies
ms.date: 03/01/2017
ms.service: reporting-services
ms.subservice: report-design
ms.topic: conceptual
ms.custom: updatefrequency5
f1_keywords:
  - "10121"
  - "sql13.rtp.rptdesigner.textboxproperties.intrctvsort.f1"
---
# Add interactive sort to a table or matrix in paginated reports (Report Builder)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-ssrs-rb](../../includes/ssrs-appliesto-ssrs-rb.md)] [!INCLUDE [ssrs-appliesto-pbi-rb](../../includes/ssrs-appliesto-pbi-rb.md)] [!INCLUDE [ssrb-applies-to-ssdt-yes](../../includes/ssrb-applies-to-ssdt-yes.md)]

  Add interactive sort buttons to enable users to change the sort order of rows and columns in tables and matrices in paginated reports. This feature is supported only in rendering formats that support user interaction, such as HTML.  
  
 When you create an interactive sort button, you must specify what to sort, what to sort by, and the scope to which to apply the sort. For example, you can sort detail rows by customer family name, subcategory group values within a category group by sales, or category and subcategory group values combined by totals.  
  
 When you view the report, columns that support interactive sorting have arrow icons that change to indicate the sort order. The first time you select an interactive sort button, items are sorted in ascending order. You can select again to toggle the sort order between ascending and descending order.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="BackToTop"></a> In this article  
 [Sort detail rows for a table with no groups](#SortingDetailRows)  
  
 [Sort a top level parent row group for a table or matrix](#SortingTopLevelParent)  
  
 [Sort child groups or detail rows for a group](#SortingChildGroups)  
  
 [Sort rows based on a complex group expression](#SortingMultipleRowGroups)  
  
 [Synchronize sort order for multiple data regions](#SynchronizingSortOrder)  
  
##  <a name="SortingDetailRows"></a> Sort detail rows for a table with no groups  
 Add an interactive sort button to a column header to enable a user to select the column header and sort the details rows in a table by the value displayed in that column.  
  
#### Add an interactive sort button to a column header and sort the table by value  
  
1.  In report design view, in a table with no groups, right-click the text box in the column header to which you want to add an interactive sort button, and then select **Text Box Properties**.  
  
1.  Select **Interactive Sorting**.  
  
1.  Select **Enable interactive sorting on this text box**.  
  
1.  In **Choose what to sort**, select **Detail rows**.  
  
1.  In **Sort by**, specify a sort expression. From the list, select the field that corresponds to the column for which you're defining a sort action. For example, for a column heading named `Title` choose `[Title]`. Specifying a sort expression is required.  
  
1.  Select **OK**.
  
1.  Repeat steps 1-6 for every column to which you want to add an interactive sort button.  
  
 To verify the sort action, choose **Run** to preview the report, and then select the interactive sort buttons.  
  
 :::image type="icon" source="/analysis-services/analysis-services/instances/media/uparrow16x16.gif"::: [Back to Top](#BackToTop)
  
##  <a name="SortingTopLevelParent"></a> Sort a top-level parent row group for a table or matrix  
 Add an interactive sort button to a column header so you can enable a user to select the column header. Then, sort the parent group rows in a table or matrix by the value displayed in that column. The order of child groups remains unchanged.  
  
#### Add an interactive sort button to a column header and sort groups  
  
1.  In a table or matrix in report design view, right-click the text box in the column header for the group to which you want to add an interactive sort button, and then select **Text Box Properties**.  
  
1.  Select **Interactive Sorting**.  
  
1.  Select **Enable interactive sorting on this text box**.  
  
1.  In **Choose what to sort**, select **Groups**.  
  
1.  From the list, select the name of the group that you're sorting. For groups based on simple group expressions, the **Sort by** value is populated with group expression.  
  
    > [!NOTE]  
    >  For complex group expressions, manually set the **Sort by** expression to the same value as the group expression.  
  
1.  Select **OK**.
  
 To verify the sort action, choose **Run** to preview the report, and then select the interactive sort buttons.  
  
  :::image type="icon" source="/analysis-services/analysis-services/instances/media/uparrow16x16.gif"::: [Back to Top](#BackToTop)
  
  
##  <a name="SortingChildGroups"></a> Sorting Child Groups or Detail Rows for a Group  
 Add an interactive sort button to a group header row to enable the user to sort the values of a child group from a parent group or to sort the detail rows for the innermost child group.  
  
#### Add an interactive sort button to a text box in a group row header and sort child groups or detail rows  
  
1.  In report design view, right-click the text box in the group header row to which you want to add an interactive sort button, and then select **Text Box Properties**.  
  
1.  Select **Interactive Sorting**.  
  
1.  Select **Enable interactive sorting on this text box**.  
  
1.  In **Choose what to sort**, choose one of the following options:  
  
    -   **Details**: Select **Details** to sort the detail rows. From the list, select the field to sort by. For this option, you must specify the value to sort by.  
  
    -   **Groups**: Select **Groups** to sort the child group values. For this option, the **Sort by** expression is automatically filled in from the group expression.  
  
1.  Select **OK**.
  
 To verify the sort action, choose **Run** to preview the report, and then select the interactive sort buttons.  
  
 :::image type="icon" source="/analysis-services/analysis-services/instances/media/uparrow16x16.gif"::: [Back to Top](#BackToTop) 
  
##  <a name="SortingMultipleRowGroups"></a> Sort rows based on a complex group expression  
 Add an interactive sort button to a column header to enable a user to select the column header and sort the combined parent and child groups. To achieve this result, you must change the group expression to be a composite of both groups. For example, suppose a matrix displays inventory totals for a store for items grouped by both color and size. To sort the rows based on the combination of color and size, you can define a group based on the combination of color and size. You can sort this way instead of having a separate group for color and a separate group for size. For more information about defining group expressions, see [Group expression examples &#40;Report Builder&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md).  
  
 In the following procedure, terms specify tablix data region areas. For more information, see [Tablix data region areas &#40;Report Builder&#41;](../../reporting-services/report-design/tablix-data-region-areas-report-builder-and-ssrs.md).  
  
 Typically, when you sort rows based on multiple groups, you want to see totals for the sorted rows, regardless of column groups. In this procedure, no column groups are used. You start by adding a matrix and removing the default column group. Alternatively, you could start by adding a table and removing the details group.  
  
#### Add an interactive sort button to a column header and sort multiple groups  
  
1.  In report design view, add a matrix.  
  
1.  Drag a numeric field to the data cell and link the dataset to the matrix.  
  
     Next, create a group with a group expression that specifies multiple fields, and a group header to use to display the group values.  
  
1.  Verify that the matrix is selected on the design surface. The **Grouping** pane displays a default row and column group.  
  
1.  In the **Row Groups** pane, right-click the default row group, and then select **Edit Group**. The **Group Properties** dialog opens.  
  
1.  In **Name**, replace the default name with a name that specifies the multiple groups that you want to group by.  
  
1.  In **Group expressions**, in **Group on**, select the Expression (**fx**) button to open the **Expression** dialog.  
  
1.  Enter the expression that specifies all fields that you want to group by. For example, the following group expression combines a field named `Color` and a field named `Size`: `=Fields!Color.Value & Fields!Size.Value`.  
  
1.  Select **OK**.
  
     You defined the group. Next, drag the fields to display to the tablix body area of the matrix. Add the fields that you chose to group by in step 7 to the tablix body area, each in its own column.  
  
     For this scenario, the first column in the tablix row groups area isn't needed. To delete the column, right-click the column header, and then select **Delete Columns**. A dialog asks whether to delete the associated groups. Select **No**. The row group area is deleted and only the tablix body area remains.  
  
     Next, remove the default column group.  
  
1. In the **Column Groups** pane, right-click the default column group, and then select **Delete Group**. A dialog asks whether to delete the group and related rows and columns or the group only. Select **Delete group only**. The column group is deleted, and the column group area is deleted. Only the tablix body area remains.  
  
     Next, add an interactive sort button to the text box that spans the matrix.  
  
1. Select the text box in the first row, and then choose **Text Box Properties**.  
  
1. Select **Interactive Sorting**.  

1. Select **Enable interactive sorting on this text box**.  
  
1. In **Choose what to sort**, select **Groups**.  
  
1. From the list, select the name of the group you created in step 5. The group expression is automatically copied to the **Sort by** text box.  
  
1. Select **OK**.
  
     You added the sort button to the text box.  
  
1. (Optional) You can suppress duplicate values in the columns that display group values. On the report design surface, select the text box that displays the value for which you want to hide repeating values. In the **Properties** pane, scroll to **HideDuplicates**, and from the list, select the name of the dataset that is linked to this matrix.  
  
 To verify the sort action, select **Run** to preview the report, and then choose the interactive sort button. The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.  
  
 :::image type="icon" source="/analysis-services/analysis-services/instances/media/uparrow16x16.gif"::: [Back to Top](#BackToTop)  
  
##  <a name="SynchronizingSortOrder"></a> Synchronize sort order for multiple data regions  
 Add an interactive sort button that enables a user to choose one sort button and sort multiple data regions. When you create an interactive sort button, you can specify whether to synchronize the sort for multiple data regions based on the same report dataset. For example, a report might include a matrix and a chart that graphically displays the data. When a user changes the sort order of the rows in the matrix, the chart automatically displays the same sort order.  
  
 To synchronize the sort order, you must use identical sort expressions for the data regions or groups to sort, and define the scope for the sort to be a mutual ancestor of both data regions. The mutual ancestor can be either the dataset to which both data regions are linked or a containing data region within which both data regions appear. For example, assume a report has both a matrix and a chart that display data from the same dataset and that are contained in a list. To synchronize the sort action, you must specify the interactive sort on a column in the matrix and set the scope to the list. When the user sorts the matrix, the chart is also sorted.  
  
#### Synchronize sort order with a chart for an interactive sort button on a matrix data region  
  
1.  In report design view, add a matrix to the report.  
  
1.  Add a numeric dataset field to the matrix data cell, for example, a field representing quantity or sales.  
  
1.  Define a row group. By default, the sort order for the group is set to the same expression as the group expression.  
  
1.  Add a chart to the report, for example, a pie chart.  
  
1.  Drag the field you chose in step 2 to the **Value** area of the **Chart Data** pane.  
  
1.  Drag the field you chose to group by to the **Category Groups** area.  
  
     The group expression for the matrix row group and the chart category group must be identical.  
  
1.  Right-click the category group, and then select **Category Group Properties**.  
  
1.  Select **Sorting**.  
  
1. Select **Add**. A new sort row is added to the sorting options grid.  
  
1. In **Sort by**, from the list, choose the same field that you chose in step 6 to group by.  
  
1. Select **OK**.
  
1. In the matrix, right-click the text box in the column header to which you want to add an interactive sort button, and then select **Text Box Properties**.  
  
1. Select **Interactive Sorting**.  
  
1. Select **Enable interactive sorting on this text box**.  
  
1. In **Choose what to sort**, select **Groups**.  
  
1. From the list under **Groups**, select the name of the group that you're sorting. The group expression for this group is automatically set for the **Sort by** value.  
  
1. Select **Also apply this sort to other groups and data regions within**. In the text box, enter the name of the dataset. For example, enter `SalesData`.  
  
1. Select **OK**.
  
 To verify the sort action, select **Run** to preview the report, and then choose the interactive sort button. The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.  
  
 :::image type="icon" source="/analysis-services/analysis-services/instances/media/uparrow16x16.gif"::: [Back to Top](#BackToTop)  
  
## Related content 
 [Filter, group, and sort data &#40;Report Builder&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Interactive sort &#40;Report Builder&#41;](../../reporting-services/report-design/interactive-sort-report-builder-and-ssrs.md)   
 [Sort data in a data region &#40;Report Builder&#41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Explore the flexibility of a Tablix data region &#40;Report Builder&#41;](../../reporting-services/report-design/exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)  
  
