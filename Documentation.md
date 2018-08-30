# Android Calculator Course for beginners
Android is a mobile OS (Operating system) that power billions of devices including but not limited to smartphones, tablets and TVs. Today, Android Pie 9.0 is the latest released from the parent company Google. In this course, we will be looking into how Android Studio works, which is the main program to build Android app and you will be on your way to making your first, fully functional Android app.

#### System requirements:
For Windows:
1.	Microsoft® Windows® 7/8/10 (32- or 64-bit)
2.	3 GB RAM minimum, 8 GB RAM recommended; plus 1 GB for the Android Emulator
3.	2 GB of available disk space minimum,
4.	4 GB Recommended (500 MB for IDE + 1.5 GB for Android SDK and emulator system image)
5.	1280 x 800 minimum screen resolution

Before we get started with Android Studio, we need to first install it.
1.	Go to https://developer.android.com/studio/
2.	Click “**Download Android Studio**”
3.	Accept the **Terms and conditions** and **Download** it
4.	Select all the **Default** options and click **Next**
5.	Once done, click **Finish** and Android Studio will start

Now you are ready to start building Android apps using Android Studio
##### STEP 1:
Click **Start a new Android Studio project**

##### STEP 2:
Configure your project
•	Type the **application name**
•	Type a company domain or use course.thetechtube.weebly.com in the Company Domain field
•	Leave the rest as default and click **Next** to proceed

##### STEP 3:
We will be selecting the minimum Android version that we want to support. For this course, we will be using **Android Lollipop 5.1**. Click on the **drop down menu** at the **Phone and Tablet** field and select **Android Lollipop 5.1** 

##### STEP 4:
Add an Activity to mobile:
Choose the **Empty Activity** then click **Next**

##### STEP 5:	
Configure Activity:
Use the default values and click **Next**

![Android Studio Image guide](https://developer.android.com/studio/images/intro/main-window_2-2_2x.png "Source: developer.android.com")

1. The **toolbar** lets you carry out a wide range of actions, including running your app and launching Android tools.

2. The **navigation bar** helps you navigate through your project and open files for editing. It provides a more compact view of the structure visible in the Project window.

3. The **editor window** is where you create and modify code. Depending on the current file type, the editor can change. For example, when viewing a layout file, the editor displays the Layout Editor.

4. The **tool window bar** runs around the outside of the IDE (Integrated development environment) window and contains the buttons that allow you to expand or collapse individual tool windows.

5. The **tool windows** give you access to specific tasks like project management, search, version control, and more. You can expand them and collapse them.

6. The **status bar** displays the status of your project and the IDE itself, as well as any warnings or messages.

In this course, we will be using only two files, **MainActivity.java** (app > java > com.weebly.thetechtube.course.calculator > MainActivity.java) and **activity_main.xml** (app > res > layout > activity_main.xml). First we will use **activity_main.xml** to setup the layout of our calculator, also known as the **User Interface**. In Android, most of the objects like Text and Image will be put into a view. For example, TextView and ImageView. And those views will be put into a Layout, for example **RelativeLaout** or **LinearLayout**.

**RelativeLayout** - In RelativeLayout, views can be positioned using margins, paddings and alignments

**LinearLayout** - In LinearLayout, every views will be positioned side-by-side either horizontally or vertically. 

Click on **activity_main.xml** file and select the **Text** option just beside the Design option.

On the right, you will see a preview screen. If not, click the **Preview** option on the right.

In the code section, we will be replacing **ConstraintLayout** with **RelativeLayout** and deleting the **TextView** code

~~~
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">



</RelativeLayout>
~~~

Before we start creating our **Calculator** app, you can create a new TextView and change the values like the **Text Size**, the **Text** itself, and changing layout_width or height from **wrap_content** to **match_parent**:
   
~~~
  <TextView
	android:id="@+id/textView1"
	android:layout_width="wrap_content"
	android:layout_height="wrap_content"
	android:text="Calculate"
	android:textSize="10sp" />
~~~

Now we will try running it on an emulator (A virtual device) for the first time. At the **toolbar**, click the **Green Play Icon**, select any virtual device, use the default values and click **Ok**. Congrats, now you officially created your very first Android app using Android Studio.

NOTE: If **Android Studio** requires you to have **Hardware Acceleration**, you can **enable** it in the **BIOS**. It will usually be in the **Advanced** > **System Options** and enable **Virtualization**.

After completing that, you can now delete the **TextView** and we will start building our **Calculator** app by typing this code inside the **RelativeLayout**:
~~~
<!-- this is a comment -->
<!-- wrap_content is where the view is wrap around the content
and match_parent is where it extents to the edge of the device -->
<!-- layout_margin means the margin will be applied to four
sides unless you specify it. For example, layout_marginTop-->

<!-- TextView is been used for Clear Button so that it could
 have a Text feel to it instead of a button-->
<TextView
    android:id="@+id/buttonClear"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="C"
    android:paddingTop="20dp"
    android:paddingBottom="25dp"
    android:layout_marginTop="5dp"
    android:layout_marginRight="5dp"
    android:layout_marginBottom="5dp"
    android:layout_marginLeft="20dp"
    android:textSize="50sp"
    android:textColor="#e4e40a"
    android:textStyle="bold"
    android:onClick="clear"/>

<!-- This TextView will be used to display info -->
<!-- Align viewEnd means it will align to the end of the view
 which is the right side-->
<TextView
    android:id="@+id/mainTextView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:paddingTop="20dp"
    android:paddingBottom="25dp"
    android:layout_toRightOf="@+id/buttonClear"
    android:layout_margin="5dp"
    android:textSize="48sp"
    android:textAlignment="viewEnd"
    android:maxLines="3"
    android:text=""/>

<!-- We will be using GridLayout to positioned our buttons-->
<!-- In GridLayout, you will need to specify how many rows
 and columns there are and each buttons will have a rowCount and
 columnCount value. More like a coordinate. The first row and
 column will start with 0 -->
<GridLayout
    android:id="@+id/gridLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_below="@+id/mainTextView"
    android:layout_marginTop="10dp"
    android:columnCount="4"
    android:rowCount="5">

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="0"
        android:layout_columnWeight="1"
        android:layout_row="0"
        android:layout_rowWeight="1"
        android:onClick="clickButton"
        android:textSize="30sp"
        android:tag="1"
        android:text="1"/>
        
    <!-- rowWeight and columnWeight represents how much space
     the view allowed to occupy -->
    <!-- Tag will be used to identify each view -->
    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="1"
        android:layout_columnWeight="1"
        android:layout_row="0"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:textSize="30sp"
        android:tag="2"
        android:text="2"/>

    <Button
        android:id="@+id/button3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="2"
        android:layout_columnWeight="1"
        android:layout_row="0"
        android:onClick="clickButton"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:tag="3"
        android:text="3"/>

    <Button
        android:id="@+id/button4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="0"
        android:layout_columnWeight="1"
        android:layout_row="1"
        android:textSize="30sp"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="4"
        android:text="4"/>

    <Button
        android:id="@+id/button5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="1"
        android:layout_columnWeight="1"
        android:layout_row="1"
        android:textSize="30sp"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="5"
        android:text="5"/>

    <Button
        android:id="@+id/button6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="2"
        android:layout_columnWeight="1"
        android:layout_row="1"
        android:textSize="30sp"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="6"
        android:text="6"/>

    <Button
        android:id="@+id/button7"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="0"
        android:layout_columnWeight="1"
        android:layout_row="2"
        android:textSize="30sp"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="7"
        android:text="7"/>

    <Button
        android:id="@+id/button8"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="1"
        android:layout_columnWeight="1"
        android:layout_row="2"
        android:textSize="30sp"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="8"
        android:text="8"/>

    <Button
        android:id="@+id/button9"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="2"
        android:layout_columnWeight="1"
        android:layout_row="2"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:textSize="30sp"
        android:tag="9"
        android:text="9"/>

    <Button
        android:id="@+id/button0"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="0"
        android:layout_columnWeight="1"
        android:layout_row="3"
        android:onClick="clickButton"
        android:textSize="30sp"
        android:layout_columnSpan="3"
        android:layout_rowWeight="1"
        android:tag="0"
        android:text="0"/>

    <Button
        android:id="@+id/buttonDot"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="0"
        android:layout_columnWeight="1"
        android:layout_row="4"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:onClick="clickButton"
        android:tag="10"
        android:text="."/>

    <!-- columnSpan or rowSpan means how much space they will take
    over. For example: There will be four columns and the columnSpan
    for buttonA is 2, so it will cover 2 columns out of four -->
    <Button
        android:id="@+id/buttonEquals"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="1"
        android:layout_columnWeight="1"
        android:layout_row="4"
        android:textSize="30sp"
        android:layout_columnSpan="2"
        android:layout_rowWeight="1"
        android:onClick="equals"
        android:text="="/>

    <Button
        android:id="@+id/buttonDelete"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="3"
        android:layout_columnWeight="1"
        android:layout_row="0"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:onClick="delete"
        android:text="DEL"/>

    <Button
        android:id="@+id/buttonPlus"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="3"
        android:layout_columnWeight="1"
        android:layout_row="1"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:onClick="clickButton"
        android:tag="11"
        android:text="+"/>

    <Button
        android:id="@+id/buttonMinus"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="3"
        android:layout_columnWeight="1"
        android:layout_row="2"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:onClick="clickButton"
        android:tag="12"
        android:text="-"/>

    <Button
        android:id="@+id/buttonMultiple"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="3"
        android:layout_columnWeight="1"
        android:layout_row="3"
        android:textSize="30sp"
        android:layout_rowWeight="1"
        android:onClick="clickButton"
        android:tag="13"
        android:text="×"/>

    <Button
        android:id="@+id/buttonDivide"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_column="3"
        android:layout_columnWeight="1"
        android:textSize="30sp"
        android:layout_row="4"
        android:onClick="clickButton"
        android:layout_rowWeight="1"
        android:tag="14"
        android:text="÷"/>

</GridLayout>
~~~

You now have complete the layout of the Calculator app. In the next section, we will be typing Java code to run everything that happens behind the scenes

~~~
package com.weebly.thetechtube.course.calculator;

public class MainActivity extends AppCompatActivity {

    Button button1;

    TextView mainTextView;
    String firstValue = "";
    String secondValue = "";
    double finalValue = 0;
    boolean firstVal = true;
    boolean firstTime = true;
    String currentOperator = "";
    int TAG;

    TextView buttonClear;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // We will be using findViewById to linked back the original
        // activity_main.xml views
        mainTextView = findViewById(R.id.mainTextView);
        buttonClear = findViewById(R.id.buttonClear);
        button1 = findViewById(R.id.button1);





        //SKIP THE BONUS SECTION FIRST, TRY CREATING IT LATER AND IF YOU 
        //NEED HELP, THIS WILL BE YOUR ANSWER
        //BONUS 1
        button1.setOnLongClickListener(new View.OnLongClickListener() {
            @Override
            public boolean onLongClick(View view) {

                mainTextView.setText("Number 1");

                return true;

            }
        });

    }

    public void equals(View view) {

        //Check for which operator is currently using, calculate
        //using the operator amd display the final value to the user
            if (currentOperator.equals("ADDITION")) {

                addition();

            } else if (currentOperator.equals("SUBTRACTION")) {

                subtraction();

            } else if (currentOperator.equals("MULTIPLICATION")) {

                multiplication();

            } else if (currentOperator.equals("DIVISION")) {

                division();

            }

            firstValue = "";
            secondValue = "";
            firstTime = false;

        //If the final value can be put into an integer than change it
        //For example: 5.0 or else use double
        if (finalValue - (int) finalValue == 0) {

            mainTextView.setText((int) finalValue + "");

        } else {

            mainTextView.setText(finalValue + "");

        }
    }






    public void clear(View view) {

       //Reset all the values back to the default
       firstValue = "";
       secondValue = "";
       finalValue = 0;
       firstVal = true;
       firstTime = true;
       currentOperator = "";
       mainTextView.setText("");

       //BONUS 3
        button1.animate().rotation(360f).setDuration(5000);

    }

    public void delete(View view) {

        //We will be deleting the last letter from a String

        //Try and catch were used to prevent the app to crashed
        //If it receives an error, it will run Catch
        try {

            if (firstVal) {

                firstValue = firstValue.substring(0, firstValue.length() - 1);
                mainTextView.setText(firstValue + "");

            } else {

                secondValue = secondValue.substring(0, secondValue.length() - 1);
                mainTextView.setText(firstValue + "");

            }

        } catch (Exception e) {

            e.printStackTrace();

        }
    }

    public void clickButton(View view) {

        //Get current TAG
            TAG = Integer.parseInt((String) view.getTag());

            Log.i("Info", "TAG = " + TAG);

            if (TAG < 10) {

                if (firstVal) {

                    //Add the TAG value to the string
                    firstValue += TAG;
                    //And display it
                    mainTextView.setText(firstValue + "");

                } else {

                    secondValue += TAG;
                    mainTextView.setText(secondValue + "");

                }
            }

            //Adding a decimal point
            // If indexOf(".") returns 0 or more means there is already
            // a decimal point while if it's a -1, it doesn't have a one
            if (TAG == 10) {

                if (firstVal) {

                    //If decimal point is not present, add it
                    if (!(firstValue.indexOf(".") >= 0)) {

                        firstValue += ".";
                        mainTextView.setText(firstValue + "");

                    }

                } else {

                    if (!(secondValue.indexOf(".") >= 0)) {

                        secondValue += ".";
                        mainTextView.setText(secondValue + "");

                    }

                }

            }


            //Addition
            if (TAG == 11) {

                if (firstTime) {

                    if (firstVal) {

                        //If firstValue is not equals to blank
                        if (!firstValue.equals("")) {

                            firstVal = false;

                        }

                    } else {

                        if (!secondValue.equals("")) {

                            checkForLastOperator();

                            addition();
                            firstTime = false;
                            firstValue = "";
                            secondValue = "";
                            firstVal = true;

                        }
                    }

                } else {

                    checkForLastOperator();

                    if (firstVal) {

                        secondValue = "";
                        addition();
                        firstVal = false;

                    } else {

                        firstValue = "";
                        addition();
                        firstVal = true;

                    }
                }


                //The addition button will be tapped so the 
                  currentOperator
                //will be ADDITION
                currentOperator = "ADDITION";

            }


        //Subtraction
        if (TAG == 12) {

            if (firstTime) {

                if (firstVal) {

                    if (!firstValue.equals("")) {

                        firstVal = false;

                    }

                } else {

                    if (!secondValue.equals("")) {

                        checkForLastOperator();

                        subtraction();
                        firstTime = false;
                        firstValue = "";
                        secondValue = "";
                        firstVal = true;

                    }
                }

            } else {

                checkForLastOperator();

                if (firstVal) {

                    secondValue = "";
                    subtraction();
                    firstVal = false;

                } else {

                    firstValue = "";
                    subtraction();
                    firstVal = true;

                }
            }

            currentOperator = "SUBTRACTION";

        }

        //Multiplication
        if (TAG == 13) {

            if (firstTime) {

                if (firstVal) {

                    if (!firstValue.equals("")) {

                        firstVal = false;

                    }

                } else {

                    if (!secondValue.equals("")) {

                        checkForLastOperator();

                        multiplication();
                        firstTime = false;
                        firstValue = "";
                        secondValue = "";
                        firstVal = true;

                    }
                }
            } else {

                   checkForLastOperator();

                    if (firstVal) {

                        secondValue = "";
                        multiplication();
                        firstVal = false;

                    } else {

                        firstValue = "";
                        multiplication();
                        firstVal = true;

                    }
            }

            currentOperator = "MULTIPLICATION";

        }

        //Division
        if (TAG == 14) {

            if (firstTime) {

                if (firstVal) {

                    if (!firstValue.equals("")) {

                        firstVal = false;

                    }

                } else {

                    if (!secondValue.equals("")) {

                        checkForLastOperator();

                        division();
                        firstTime = false;
                        firstValue = "";
                        secondValue = "";
                        firstVal = true;

                    }
                }

            } else {

                checkForLastOperator();


                if (firstVal) {

                    secondValue = "";
                    division();
                    firstVal = false;

                } else {

                    firstValue = "";
                    division();
                    firstVal = true;

                }
            }

            currentOperator = "DIVISION";

        }
    }
    public void addition() {

        //Check if first or second value are blank then add a 0 to it
        if (!firstTime)  {

            if (firstValue.equals("")) {

                firstValue = "0";

            }

            if (secondValue.equals("")) {

                secondValue = "0";

            }

        }

       try {

           finalValue += Double.parseDouble(firstValue) + Double.parseDouble(secondValue);

           firstValue = "";
           secondValue = "";

       } catch (Exception e) {

            e.printStackTrace();

       }
    }




    public void subtraction() {

        if (!firstTime)  {

            if (firstValue.equals("")) {

                firstValue = "0";

            }

            if (secondValue.equals("")) {

                secondValue = "0";

            }
        }

        try {

            //If the finalValue equals to 0 and the firstTime equals true
            if (finalValue == 0 && firstTime) {

                finalValue = Double.parseDouble(firstValue) - Double.parseDouble(secondValue);

            } else {

                    finalValue -= Double.parseDouble(firstValue);

                    finalValue -= Double.parseDouble(secondValue);

            }

            firstValue = "";
            secondValue = "";

        } catch (Exception e) {

            e.printStackTrace();

        }
    }

    public void multiplication() {

        //Check if first or second value are blank then add a 1 to it
        //If we add 0, the final answer will appear to be 0
        if (!firstTime)  {

            if (firstValue.equals("")) {

                firstValue = "1";

            }

            if (secondValue.equals("")) {

                secondValue = "1";

            }

        }


        try {

            if (finalValue == 0 && firstTime) {

                finalValue = Double.parseDouble(firstValue) * Double.parseDouble(secondValue);

            } else {

                if (firstVal) {
                    finalValue *= Double.parseDouble(firstValue);
                } else {
                    finalValue *= Double.parseDouble(secondValue);
                }
            }

            firstValue = "";
            secondValue = "";

        } catch (Exception e) {

            e.printStackTrace();

        }

    }

    public void division() {

        //Check if first or second value are blank then add a 1 to it
        //If we add 0, the final answer will appear to be infinity
        if (!firstTime) {

            if (firstValue.equals("")) {

                firstValue = "1";

            }

            if (secondValue.equals("")) {

                secondValue = "1";

            }

        }

        try {

            if (finalValue == 0 && firstTime) {

                finalValue = Double.parseDouble(firstValue) / Double.parseDouble(secondValue);

            } else {

                if (firstVal) {
                    finalValue /= Double.parseDouble(firstValue);
                } else {
                    finalValue /= Double.parseDouble(secondValue);
                }
            }
            firstValue = "";
            secondValue = "";

        } catch (Exception e) {

            e.printStackTrace();

        }


    }

    //To check if previously used operator exists
    public void checkForLastOperator() {

        if (currentOperator.equals("ADDITION")) {

            addition();
            Log.i("Info addition", String.valueOf(finalValue));

        } else if (currentOperator.equals("SUBTRACTION")) {

            subtraction();
            Log.i("Info subtraction", String.valueOf(finalValue));

        } else if (currentOperator.equals("MULTIPLICATION")) {

            multiplication();
            Log.i("Info multiplication", String.valueOf(finalValue));

        } else if (currentOperator.equals("DIVISION")) {

            division();
            Log.i("Info division", String.valueOf(finalValue));

        }

    }

    //BONUS SECTION

    /** 1. TRY to show a message in the mainTextView when
     *  a particular button is being long pressed
     *
     * STEP 1: Create a new button name at the start of the code,
     *         we will be linking the button name with the
     *         activity_main.xml button
     *
     *         For example: Button button1;
     *
     *         Then, add this line of code to the onCreate method
     *
     *         button1 = findViewById(R.id.button1);
     *
     * STEP 2: Once completed, we will call button1 long click listener
     *         to check if there is a long pressed occur for that button
     *
     *         Question:  If someone performs a click is called 
     *                    onClickListener
     *         What will long press be called?
     *
     *         Answer: NOTE replace return false to true if exists
     *         button1.setOnLongClickListener(new 
     *         View.OnLongClickListener() {
     *         @Override
     *         public boolean onLongClick(View view) {
     *
     *         mainTextView.setText("Number 1");
     *         return true;
     *
     *            }
     *         });
     *
     * STEP 3: Run your app now on an emulator or a real device to see 
     *         the results
     *
     * Now try doing the same things but for different buttons
     * */

    /** 2. Now try playing with the xml code in activity_main.xml
     *     Change and add things like textColor, fontSize, layout_width,
     *     layout_height and the text itself
     *
     *     Samples:
     *
     *     - android:textColor="#FFFFFF"
     *     - android:layout_width="100dp"
     *     - android:textSize="20sp"
     *     - android:scaleX="2"
     *     - android:scaleY="2"
     */




    /** 3. Let's try animating the buttons when you press the Clear button
     *
     *       Now we are animating button1, rotation 360 means turning it 
     *       360 degress
     *       and the value will be in a float Type and the duration is
     *       5 seconds. 1s = 1000ms. So now, add this code to your Clear 
     *       method
     *

     *       //It will only run once
     *       button1.animate().rotation(360f).setDuration(5000);
     *
     *       Try setting different commands like alpha and setting other 
     *       buttons and even TextViews too.
     *       REMEMBER to link it to the activity_main.xml
     *
     */

    //Congrats, you just wrote more than 600 lines of code.
    //Now, it's time to show the world what you had build
    //Once again, thanks for trying out our Android app course

}
~~~

![Creative Commons Attribution-ShareAlike 4.0 International License Logo](https://i.creativecommons.org/l/by-sa/4.0/80x15.png "Creative Commons Attribution-ShareAlike 4.0 International License Logo")
This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License

For more information about the license, please visit:
https://creativecommons.org/licenses/by-sa/4.0/

Developed and published by The Tech Tube.
To share, modify and published our content.
You must attribute the original creator which is
Lj Yeoh and The Tech Tube and with your own name
if you decide to modify and published it.

Our current website: https://thetechtube.weebly.com/
Source: developer.android.com