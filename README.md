# <b>Predominance Toolset</b></center>

The <b>Predominance Tool</b> prompts you to input the fields you are interested in and reports the predominant value. To run the full tool, you will need to first utilize the <b>“Calculate Gap”</b> tool which calculates the first and second highest numbers in a list of fields and outputs the gap between these two numbers. Then, the <b>“Calculate Predominance”</b> tool incorporates the gap value calculated in the first tool. The gap represents the difference between the largest value and the second largest value. The collection of these gap numbers are compared throughout the dataset in order to measure if the predominance is significant or not. The user can specify 1 of 3 options to determine significance: (1) Should the gap be larger than the mean of all gaps to be considered significant?, (2) Should the gap be greater than a specified standard deviation over the mean to be significant?, or (3) Should the percentage of the gap be greater than a user-specified value to be considered significant?

The rest of this document will address the specifics of each tool.

### 1. The Calculate Gap Tool

This tool finds the first and second highest numbers in a list of inputted fields and outputs the gap (or difference) between these two numbers. 

![alt tag](https://cloud.githubusercontent.com/assets/10080810/7265717/33775b14-e853-11e4-87d8-a8d306b667f8.png)

The first step is to click on the manila folder to select a feature class. A list of fields should pop up in the box below. Select the fields you are interested in comparing. After, click “OK” to run the tool.

The tool adds 7 fields to your feature class. To view these fields, right click on the feature class in the Table of Contents and click “Open Attribute Table”. The following is an explanation of each of the <b>added fields</b>:

1.	<b>Dominant Component</b> (DomFName): The name of the field with the highest value.
2.	<b>Dominant Component Alias</b> (DomFAlias): The alias of the field with the highest value.
3.	<b>Dominant Value</b> (DomValue): The value of the dominant field. 
4.	<b>Margin of Dominance</b> (DomMarg): The difference between the first and second highest values.
5.	<b>% Dominance</b> (DomPerc): The percent of the total values the dominant value represents. Calculated by dividing the maximum value by the total value of all selected fields.
6.	<b>Transparency</b> (DomPerXP): The transparency of the dominant field. Calculated by subtracting the dominant percent from 100 (e.g., if the dominant field is 80% of the total values, the transparency will be 20%. If the highest value is only 30% of the total value, it will have a higher transparency of 70%.)
7.	<b># of Ties</b> (DomFCnt): The number of fields with the same value.

![alt tag](https://cloud.githubusercontent.com/assets/10080810/7265723/54a0db44-e853-11e4-8ead-61c440e0b898.png)

### 2. The Calculate Predominance Tool

This tool uses the gap (or Margin of Dominance) output from the previous tool to calculate the predominant value. The tool allows the user to specify three options to determine whether a maximum value is considered significant.

![alt tag](https://cloud.githubusercontent.com/assets/10080810/7265727/6560bd3c-e853-11e4-95c8-a8e2e7ab797e.png)

First, input the feature class you are interested in analyzing. This should be the same feature class you used in the Calculate Gap tool. Next, choose a predominance option that tells the tool what criteria the maximum field must meet to be considered significant. The three options are as follows:

1.	<b>Over the mean</b> (OVER_MEAN): Compares each predominance gap to the mean of all gap values within the dataset.
2.	<b>Over the mean + standard deviation</b> (OVER_STD): Compares each predominance gap to the mean of all gap values plus an additional standard deviation. The choices for the standard deviation are 1, .5, or .33.
3.	<b>Over a user-specified value</b> (USER_SPEC): Compares the gap to a user-inputted value.

If the user-specified value is selected as the Predominance Option, enter the value. If you are not using a specified value, leave this section blank. If using the standard deviation option, choose between 1, .5, or .33 from the dropdown menu. After, click “OK” to run the tool.

The tool <b>adds fields</b> to the attribute table depending on which Predominance Option you choose:

1.	If using <b>“Over the mean”</b>:
    * <b>Mean Gap</b> (MeanGap): Calculates the average gap value of all the dominant margins.
    * <b>Predominant Field Over Mean Gap</b> (DomOverMean): Outputs the predominant field if it meets the requirement of being over the mean gap value. If not, it outputs “No Predominance Over Mean”.
    * <b>Predominant Field Alias Over Mean Gap</b> (MeanDomAlias): Outputs the alias of the predominant field if it meets the requirement of being over the mean gap value. If not, it outputs “No Predominance Over Mean”.
    * <b>Mean Gap Transparency</b> (MeanGapTrans): If the predominant field meets the significance requirement, the transparency is set to 0. If not, the transparency is calculated with the following equation: ((average gap – gap)/average gap)*100)

2.	If using “Over the mean + 1 standard deviation”:
    * <b>1 Std Gap</b> (OneSDGap): Calculates the average gap value plus one standard deviation of all the dominant margins.
    * <b>Predominant Field within 1 Std Dev</b> (Dom1SD): Outputs the predominant field if it meets the requirement of being over the mean gap value plus one standard deviation. If not, it outputs “No Predominance Within 1.0 Standard Deviation”.
    * <b>Predominance Field Alias Over 1 SD</b> (SD1DomAlias): Outputs the alias of the predominant field if it meets the requirement of being over the mean gap value plus one standard deviation. If not, it outputs “No Predominance Within 1.0 Standard Deviation”.
    * <b>Dominance Transparency Using 1 SD</b> (SD1DomTrans): If the predominant field meets the significance requirement, the transparency is set to 0. If not, the transparency is calculated with the following equation: ((average gap – gap)/average gap)*100)

3.	If using “Over the mean + .5 standard deviation”:
    * <b>Half Std Gap</b> (HalfSDGap): Calculates the average gap value plus a half standard deviation of all the dominant margins.
    * <b>Predominant Field within Half Std Dev</b> (DomHalfSD): Outputs the predominant field if it meets the requirement of being over the mean gap value plus a half standard deviation. If not, it outputs “No Predominance Within 0.5 Standard Deviation”.
    * <b>Predominance Field Alias Over Half SD</b> (HalfSDDomAlias): Outputs the alias of the predominant field if it meets the requirement of being over the mean gap value plus a half standard deviation. If not, it outputs “No Predominance Within 0.5 Standard Deviation”.
    * <b>Dominance Transparency Using Half SD</b> (HalfSDDomTrans): If the predominant field meets the significance requirement, the transparency is set to 0. If not, the transparency is calculated with the following equation: ((average gap – gap)/average gap)*100)

4.	If using “Over the mean + .33 standard deviation”:
    * <b>Third Std Gap</b> (ThirdSDGap): Calculates the average gap value plus a third standard deviation of all the dominant margins.
    * <b>Predominant Field wihin Third Std Dev</b> (DomThirdSD): Outputs the predominant field if it meets the requirement of being over the mean gap value plus a third standard deviation. If not, it outputs “No Predominance Within 0.33 Standard Deviation”.
    * <b>Predominance Field Alias Over Third SD</b> (ThirdSDDomAlias): Outputs the alias of the predominant field if it meets the requirement of being over the mean gap value plus a third standard deviation. If not, it outputs “No Predominance Within 0.33 Standard Deviation”.
    * <b>Dominance Transparency Using Third SD</b> (ThirdSDDomTrans): If the predominant field meets the significance requirement, the transparency is set to 0. If not, the transparency is calculated with the following equation: ((average gap – gap)/average gap)*100)

5.	If using “Over a user-specified value”:
    * <b>User Specified Gap</b> (SpecGap): Fills each row with the gap value that the user specified.
    * <b>Predominant Field Over Specified Gap</b> (DomOverSpec): Outputs the predominant field if it meets the requirement of being over the user-inputted value. If not, it outputs “No Predominance Over Specified Gap”.
    * <b>Predominant Field Alias Over Specified Gap</b> (UserDomAlias): Outputs the alias of the predominant field if it meets the requirement of being over the user-inputted value. If not, it outputs “No Predominance Over Specified Gap”.
    * <b>Specified Gap Transparency Value</b> (SpecGapTrans): If the predominant field meets the significance requirement, the transparency is set to 0. If not, the transparency is calculated with the following equation: ((average gap – gap)/average gap)*100)

### 3. Mapping Predominance

After running the <b>Calculate Gap Tool</b>and the <b>Calculate Predominance tool</b>, try mapping the predominant fields. To do this, right-click on the feature class in the Table of Contents and click on “Properties”. Go to the “Symbology” tab and click on the “Categories” section. In the Value Field, choose the field that was outputted from the Calculate Predominance tool (e.g., Predominant Field Over Mean Gap). Click “Add All Values”. Then click on the “Advanced” button to enable a transparency rule. Choose the field related to transparency (e.g., Mean Gap Transparency Value). Click “OK” to see the results on the map. 

This type of predominance mapping is beneficial in showing <i>how</i> much more dominant one area is when compared to another. The solid areas (with less transparency) have a greater predominance gap than areas that are more transparent. One example of this type of mapping can be found in this <b>[predominant race map](http://urbanobservatory.maps.arcgis.com/home/webmap/viewer.html?layers=0fd7dc7c53c34b03ab4475d895b5d32f&useExisting=1 "Predominant Population Map")</b>. 



