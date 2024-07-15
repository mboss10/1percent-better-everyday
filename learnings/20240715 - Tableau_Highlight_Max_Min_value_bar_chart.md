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

I have published a dashboard on Tableau Public that can be seen <a href="https://public.tableau.com/views/HighlightMaxMinExamples/HighlightMaxMinDash?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link" target="_blank">here</a>  

The workbook is also available in here on GitHub

<div class='tableauPlaceholder' id='viz1721085877162' style='position: relative'><noscript><a href='#'><img alt='HighlightMaxMinDash ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Hi&#47;HighlightMaxMinExamples&#47;HighlightMaxMinDash&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='HighlightMaxMinExamples&#47;HighlightMaxMinDash' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Hi&#47;HighlightMaxMinExamples&#47;HighlightMaxMinDash&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>                <script type='text/javascript'>                    var divElement = document.getElementById('viz1721085877162');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='1200px';vizElement.style.height='827px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='1200px';vizElement.style.height='827px';} else { vizElement.style.width='100%';vizElement.style.height='1427px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>

### **Conclusion**

By following these steps, you can effectively highlight the maximum and minimum values in your Tableau bar chart, making it easier to identify key data points at a glance. This technique can be particularly useful in dashboards and reports where visual emphasis on extreme values is important.
