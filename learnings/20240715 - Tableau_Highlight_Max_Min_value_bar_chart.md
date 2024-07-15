## Highlighting Max and Min Values in a Tableau Bar Chart

Highlighting the maximum and minimum values in a Tableau bar chart can help emphasize key data points. This guide will walk you through the steps to achieve this.

### **Step-by-Step Guide**

#### **1. Create a Calculated Field**

First, you need to create a calculated field to identify the max and min values in your dataset.

1. Go to the **Data** pane, right-click, and select **Create Calculated Field**.
2. Name the calculated field (e.g., "MaxMin Highlight").
3. Enter the following formula:
    ```sql
    IF SUM([YourMeasure]) = WINDOW_MAX(SUM([YourMeasure])) THEN "Max"
    ELSEIF SUM([YourMeasure]) = WINDOW_MIN(SUM([YourMeasure])) THEN "Min"
    ELSE "Other"
    END
    ```
   Replace `[YourMeasure]` with the field you are analyzing.

#### **2. Add the Calculated Field to the Color Shelf**

Next, you need to use this calculated field to color the bars.

1. Drag the newly created calculated field ("MaxMin Highlight") to the **Color** shelf on the **Marks** card.
2. Tableau will automatically assign different colors to "Max", "Min", and "Other".

#### **3. Customize Colors**

To make the max and min values stand out, customize the colors:

1. Click on the **Color** legend.
2. Choose **Edit Colors**.
3. Assign distinct colors to "Max" and "Min" (e.g., red for max, green for min) and a neutral color for "Other".

#### **4. Label the Max and Min Values**

To further highlight these values, you can add labels:

1. Click on the **Label** button on the **Marks** card.
2. Check the box for **Show mark labels**.
3. Click on **Label** again and choose **Min/Max** from the **Marks to Label** section.
4. Customize the label appearance as needed.

#### **5. Adjust the Scope (Optional)**

If you need to adjust the scope of the min/max calculation (e.g., per pane, per cell):

1. Click on the **Label** button on the **Marks** card.
2. In the **Marks to Label** section, select the appropriate scope (e.g., **Table**, **Pane**, **Cell**).

### **Example**

Here is an example of how the calculated field might look in practice:

```sql
IF SUM([Sales]) = WINDOW_MAX(SUM([Sales])) THEN "Max"
ELSEIF SUM([Sales]) = WINDOW_MIN(SUM([Sales])) THEN "Min"
ELSE "Other"
END
```

### **Conclusion**

By following these steps, you can effectively highlight the maximum and minimum values in your Tableau bar chart, making it easier to identify key data points at a glance. This technique can be particularly useful in dashboards and reports where visual emphasis on extreme values is important.
