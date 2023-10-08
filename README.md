## **UnitConverterMAUI**

This is a View navigation focused project led by Hector Perez on his Udemy course: *.NET MAUI course with Visual Studio 2022 creating PROJECTS*

There are 2 Views that establish the application:
- *MenuView*
  - A primary Grid container with 3 columns and 4 rows
    - Row 1 simply dispays the app's title, spanning all columns
    - The remaining 3 rows are broken down into each of the conversion categories, with FontImageSource Images from a loaded font *fontello* and TapGestureRecognizer Events attached to each as means of passing to their corresponding View
  - **The Codebehind**
    - *TapGestureRecognizer_Tapped()* captures the desired Label.Text value in *option* and passes it to the ConverterViewModel() Constructor
      - It then navigates to the ConverterView using the desired unit category
- *ConverterView*
  - A primary Grid container broken into 2 rows
    - Row 1 displays the Entry and Picker where the user can select the units and values they want to see converted
    - Row 2 displays the conversion, along with another Picker to change the selected conversion unit type
  - All information is dynamically bound to the ViewModel so that only one View is required to display all requested information, rather than building out a View for each category
  - The Pickers implement SelectedIndexChanged so their selected unit will update displayed information
  - **The Codebehind**
    - *Picker_SelectedIndexChanged()* updates the Picker's value by calling the *Convert()* Method from *ConverterViewModel*

*ConverterViewModel* handles the logic of the application, utilizing the *UnitsNet* and *Fody* Nuget Packages. *UnitsNet* houses the logic for conversions and *Fody* implements *INotifyPropertyChanged* without needing any additional code.
- The Constructor was overloaded to assign default values for when *ConverterView* is initially loaded.
- *Convert()* puts *UnitsNet* to work and calculates converted values
- *LoadMeasures()* selects the category from *MenuView()* and loads the List of units to the Pickers
