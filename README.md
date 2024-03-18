# PSoC&trade; 4: MSCLP low-power mutual-capacitance button

This code example demonstrates how to use the CAPSENSE&trade; middleware to detect a finger touch on a mutual-capacitance-based button widget in PSoC&trade; 4000T device with a multi-sense converter low-power (MSCLP) CAPSENSE&trade; block.

In addition, this code example also explains how to manually tune the mutual-capacitance-based button for optimum performance with respect to parameters such as reliability, power consumption, and response time using the CSX-RM sensing technique and CAPSENSE&trade; Tuner GUI. Here, CSX represents the mutual-capacitance sensing technique, and RM represents the ratiometric method.

[View this README on GitHub.](https://github.com/Infineon/mtb-example-psoc4-msclp-low-power-csx-button)

[Provide feedback on this code example.](https://cypress.co1.qualtrics.com/jfe/form/SV_1NTns53sK2yiljn?Q_EED=eyJVbmlxdWUgRG9jIElkIjoiQ0UyMzg4MjAiLCJTcGVjIE51bWJlciI6IjAwMi0zODgyMCIsIkRvYyBUaXRsZSI6IlBTb0MmdHJhZGU7IDQ6IE1TQ0xQIGxvdy1wb3dlciBtdXR1YWwtY2FwYWNpdGFuY2UgYnV0dG9uIiwicmlkIjoieWFzaHZpIiwiRG9jIHZlcnNpb24iOiIyLjAuMCIsIkRvYyBMYW5ndWFnZSI6IkVuZ2xpc2giLCJEb2MgRGl2aXNpb24iOiJNQ0QiLCJEb2MgQlUiOiJJQ1ciLCJEb2MgRmFtaWx5IjoiUFNPQyJ9)


## Requirements

- [ModusToolbox&trade;](https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software/) v3.2 or later

 > **Note:** This code example version requires ModusToolbox&trade; version 3.2 or later and is not backward compatible with v3.1 or older versions.

- Board support package (BSP) minimum required version: 3.2.0
- Programming language: C
- Associated parts: [PSoC&trade; 4000T](https://www.infineon.com/002-33949)

## Supported toolchains (make variable 'TOOLCHAIN')

- GNU Arm&reg; Embedded Compiler v11.3.1 (`GCC_ARM`) - Default value of `TOOLCHAIN`
- Arm&reg; Compiler v6.16 (`ARM`)
- IAR C/C++ Compiler v9.30.1 (`IAR`)

## Supported kits (make variable 'TARGET')

- [PSoC&trade; 4000T CAPSENSE&trade; Prototyping Kit](https://www.infineon.com/CY8CPROTO-040T) (`CY8CPROTO-040T`) - Default `TARGET`

## Hardware setup

This example uses the board's default configuration. See the [Kit user guide](https://www.infineon.com/002-38600) to ensure that the board is configured correctly to use VDDA at 5 V.

## Software setup

See the [ModusToolbox&trade; tools package installation guide](https://www.infineon.com/ModusToolboxInstallguide) for information about installing and configuring the tools package.


This example requires no additional software or tools.

## Using the code example

### Create the project

The ModusToolbox&trade; tools package provides the Project Creator as both a GUI tool and a command line tool.

<details><summary><b>Use Project Creator GUI</b></summary>

1. Open the Project Creator GUI tool.

   There are several ways to do this, including launching it from the dashboard or from inside the Eclipse IDE. For more details, see the [Project Creator user guide](https://www.infineon.com/ModusToolboxProjectCreator) (locally available at *{ModusToolbox&trade; install directory}/tools_{version}/project-creator/docs/project-creator.pdf*).

2. On the **Choose Board Support Package (BSP)** page, select a kit supported by this code example. See [Supported kits](#supported-kits-make-variable-target).

   > **Note:** To use this code example for a kit not listed here, you need to update the source files. If the kit does not have the required resources, the application may not work.

3. On the **Select Application** page:

   a. Select the **Applications(s) Root Path** and the **Target IDE**.

   > **Note:** Depending on how you open the Project Creator tool, these fields may be pre-selected.

   b.Select this code example from the list by enabling its check box.

   > **Note:** Narrow the list of displayed examples by typing in the filter box.

   c. (Optional) Change the suggested **New Application Name** and **New BSP Name**.

   d. Click **Create** to complete the application creation process.

</details>

<details><summary><b>Use Project Creator CLI</b></summary>

The 'project-creator-cli' tool can be used to create applications from a CLI terminal or from within batch files or shell scripts. This tool is available in the *{ModusToolbox&trade; install directory}/tools_{version}/project-creator/* directory.

Use a CLI terminal to invoke the 'project-creator-cli' tool. On Windows, use the command-line 'modus-shell' program provided in the ModusToolbox&trade; installation instead of a standard Windows command-line application. This shell provides access to all ModusToolbox&trade; tools. You can access it by typing "modus-shell" in the search box in the Windows menu. In Linux and macOS, you can use any terminal application.

The following example clones the "[MSCLP low-power CSX button tuning](https://github.com/Infineon/mtb-example-psoc4-msclp-low-power-csx-button)" application with the desired name "MSCLPMutualCapButtonTuning" configured for the *CY8CPROTO-040T* BSP into the specified working directory, *C:/mtb_projects*:

   ```
   project-creator-cli --board-id CY8CPROTO-040T --app-id mtb-example-psoc4-msclp-low-power-csx-button --user-app-name MSCLPMutualCapButtonTuning --target-dir "C:/mtb_projects"
   ```

The 'project-creator-cli' tool has the following arguments:

Argument | Description | Required/optional
---------|-------------|-----------
`--board-id` | Defined in the <id> field of the [BSP](https://github.com/Infineon?q=bsp-manifest&type=&language=&sort=) manifest | Required
`--app-id`   | Defined in the <id> field of the [CE](https://github.com/Infineon?q=ce-manifest&type=&language=&sort=) manifest | Required
`--target-dir`| Specify the directory in which the application is to be created if you prefer not to use the default current working directory | Optional
`--user-app-name`| Specify the name of the application if you prefer to have a name other than the example's default name | Optional

> **Note:** The project-creator-cli tool uses the `git clone` and `make getlibs` commands to fetch the repository and import the required libraries. For details, see the "Project creator tools" section of the [ModusToolbox&trade; tools package user guide](https://www.infineon.com/ModusToolboxUserGuide) (locally available at {ModusToolbox&trade; install directory}/docs_{version}/mtb_user_guide.pdf).

</details>



### Open the project

After the project has been created, you can open it in your preferred development environment.


<details><summary><b>Eclipse IDE</b></summary>

If the Project Creator tool is opened from the included Eclipse IDE, the project will open in Eclipse automatically.

For more details, see the [Eclipse IDE for ModusToolbox&trade; user guide](https://www.infineon.com/MTBEclipseIDEUserGuide) (locally available at *{ModusToolbox&trade; install directory}/docs_{version}/mt_ide_user_guide.pdf*).

</details>


<details><summary><b>Visual Studio (VS) Code</b></summary>

Launch VS Code manually, and then open the generated *{project-name}.code-workspace* file located in the project directory.

For more details, see the [Visual Studio Code for ModusToolbox&trade; user guide](https://www.infineon.com/MTBVSCodeUserGuide) (locally available at *{ModusToolbox&trade; install directory}/docs_{version}/mt_vscode_user_guide.pdf*).

</details>


<details><summary><b>Keil µVision</b></summary>

Double-click the generated *{project-name}.cprj* file to launch the Keil µVision IDE.

For more details, see the [Keil µVision for ModusToolbox&trade; user guide](https://www.infineon.com/MTBuVisionUserGuide) (locally available at *{ModusToolbox&trade; install directory}/docs_{version}/mt_uvision_user_guide.pdf*).

</details>


<details><summary><b>IAR Embedded Workbench</b></summary>

Open IAR Embedded Workbench manually, and create a new project. Then select the generated *{project-name}.ipcf* file located in the project directory.

For more details, see the [IAR Embedded Workbench for ModusToolbox&trade; user guide](https://www.infineon.com/MTBIARUserGuide) (locally available at *{ModusToolbox&trade; install directory}/docs_{version}/mt_iar_user_guide.pdf*).

</details>


<details><summary><b>Command line</b></summary>

If you prefer to use the CLI, open the appropriate terminal, and navigate to the project directory. On Windows, use the command-line 'modus-shell' program; on Linux and macOS, you can use any terminal application. From there, you can run various `make` commands.

For more details, see the [ModusToolbox&trade; tools package user guide](https://www.infineon.com/ModusToolboxUserGuide) (locally available at *{ModusToolbox&trade; install directory}/docs_{version}/mtb_user_guide.pdf*).

</details>


## Operation

1. Connect the board to your PC using the provided micro USB cable through the KitProg3 USB connector as shown in Figure 1.

    **Figure 1. Connecting the [CY8CPROTO-040T](https://www.infineon.com/CY8CPROTO-040T) kit with the PC**

   <img src="images/psoc4000t_kit_connected.jpg" alt="" width="400" />

   


2. Program the board using one of the following:

   <details><summary><b>Using Eclipse IDE</b></summary>

      1. Select the application project in the Project Explorer.

      2. In the **Quick Panel**, scroll down, and click **\<Application Name> Program (KitProg3_MiniProg4)**.
   </details>


   <details><summary><b>In other IDEs</b></summary>

   Follow the instructions in your preferred IDE.
   </details>


   <details><summary><b>Using CLI</b></summary>

     From the terminal, execute the `make program` command to build and program the application using the default toolchain to the default target. The default toolchain is specified in the application's Makefile but you can override this value manually:
      ```
      make program TOOLCHAIN=<toolchain>
      ```

      Example:
      ```
      make program TOOLCHAIN=GCC_ARM
      ```
   </details>

3. After programming, the application starts automatically.

   > **Note:** After programming, you see the following error message if Debug mode is disabled. Ignore the error or enable the Debug mode to resolve this error.

   ``` c
   "Error: Error connecting Dp: Cannot read IDR"
   ```

4. To test the application, place your finger over the CAPSENSE&trade; button and notice that the LED2 turns ON when touched and turns OFF when the finger is lifted.

5. You can also monitor the CAPSENSE&trade; data using the CAPSENSE&trade; tuner application as follows:

    **Monitor data using CAPSENSE&trade; Tuner**
    
    1. Open CAPSENSE&trade; Tuner from the **Tools** section in the IDE **Quick Panel**. 
    
        You can also run the CAPSENSE&trade; tuner application standalone from *{ModusToolbox&trade; install directory}/ModusToolbox/tools_{version}/capsense-configurator/capsense-tuner*. In this case, after opening the application, select **File** > **Open** and open the *design.cycapsense* file of the respective application, which is present in the *{Application root directory}/bsps/TARGET_APP_\<BSP-NAME>/config/* folder. 

	     See the [ModusToolbox&trade; user guide](https://www.infineon.com/ModusToolboxUserGuide) (locally available at *ModusToolbox&trade; install directory/docs_{version}/mtb_user_guide.pdf*) for options to open the CAPSENSE&trade; tuner application using the CLI.

    2. Ensure that the kit is in **CMSIS-DAP Bulk mode** (KitProg3 status LED is ON and not blinking). See [Firmware-loader](https://github.com/Infineon/Firmware-loader) to learn how to update the firmware and switch modes in KitProg3.
  
    3. In the tuner application, click on the **Tuner Communication Setup** icon or select **Tools** > **Tuner Communication Setup**. In the window, select the I2C checkbox under KitProg3 and configure as shown in Figure 2.

       - **I2C address:** 8
       - **Sub-address:** 2 bytes
       - **Speed (kHz):** 400

        These are the same values set in the EZI2C resource.

        **Figure 2. Tuner Communication Setup parameters**

       <img src="images/tuner-comm-settings.png" alt="" width="500" />

        <br>

    4. Click **Connect** or select **Communication** > **Connect** to establish a connection as shown in Figure 3.

       **Figure 3. Establish connection**

        <img src="images/tuner-connect.png" alt="" width="400" />

        <br>

    5. Click **Start** or select **Communication** > **Start** to start data streaming from the device.

         **Figure 4. Start Tuner communication**

         <img src="images/tuner-start.png" alt="" width="400" />

         <br>

         The **Widget/Sensor parameters** tab gets updated with the parameters configured in the **CAPSENSE&trade; Configurator** window. The tuner displays the data from the sensor in the **Widget View** and **Graph View** tabs.

         <br>

    6. Set the **Read mode** to **Synchronized** mode. Navigate to the **Widget View** tab, and you can see the **Button0** widget highlighted in **blue** when you touch it as shown in Figure 5.

       **Figure 5. Widget View of the CAPSENSE&trade; Tuner**

         <img src="images/tuner-widget-view.png" alt="" width="600"/>

         <br>

    7. You can view the raw count, baseline, difference count, and status for each sensor in the **Graph View** tab. For example, to view the sensor data for Button0, select **Button0_Rx0** under **Button0**.

       **Figure 6. Graph View for the CAPSENSE&trade; Tuner**

       <img src="images/tuner-graph-view-intro.png" alt="" width="600"/>

       <br>

    8. Observe the **Widget/Sensor parameters** section in the CAPSENSE&trade; Tuner window as shown in Figure 6.
      
    9. Switch to the **SNR Measurement** tab for measuring the SNR, verify that the SNR is greater than 5:1 and the signal count is above 50, select the **Button0** and **Button0_Rx0** sensors, and then click **Acquire Noise** as shown in Figure 7.

       **Figure 7. CAPSENSE&trade; Tuner – SNR measurement: Acquire noise**

       <img src="images/tuner-acquire-noise.png" alt="" width="600"/>

       <br>

    10. Once the noise is acquired, place the metal finger (6 mm finger is used in this example) at a position on the button and then click **Acquire Signal**. Ensure that the metal finger remains on the button as long as the signal acquisition is in progress. Observe that the SNR is above 5:1 and the signal count is above 50.

        The calculated SNR on this button is displayed as shown in Figure 8. Based on your end- system design, test the signal with a finger that matches the size of your normal use case. Typically, finger-size targets are ~4 to 8 mm. Consider testing with smaller sizes that should be rejected by the system to ensure that they do not reach the finger threshold.

        **Figure 8. CAPSENSE&trade; Tuner - SNR measurement: Acquire signal**

        <img src="images/tuner-acquire-signal.png" alt="" width="600"/>

        <br>

        > **Note :** Refer to the [PSoC&trade; 4: MSCLP low-power CSD button](https://github.com/Infineon/mtb-example-psoc4-msclp-low-power-csd-button) to observe these power state transitions, indicated by changing the blinking rate of a LED.

</details>

<br>

## Operation at other voltages

[CY8CPROTO-040T](https://www.infineon.com/CY8CPROTO-040T) supports operating voltages of 1.8 V, 3.3 V, and 5 V. Refer to the [Kit user guide](https://www.infineon.com/002-38600) to set the preferred operating voltage and refer to section [setup the VDDA supply voltage and Debug mode](#set-up-the-vdda-supply-voltage-and-debug-mode-in-device-configurator).

This application's functionalities are optimally tuned for 5 V. However, basic functionalities works on other voltages. 

For better performance, tune the application according to the preferred voltages.

## Measure current at different power modes

See the code example [CE238817](https://github.com/Infineon/mtb-example-psoc4-msclp-low-power-csd-button) that describes the steps of current measurement at different power modes.

#### Table 1. Measured current for different modes

Power mode | Refresh rate (Hz) | Current consumption (µA)
---------|-------------|-----------
Active    |128    | 66
Active low-refresh rate <br>(ALR)  |32 | 18
Wake-on-Touch <br>(WoT)  |16 | 3.0

> **Note :** The above WoT current was measured on a kit having Deep Sleep current of 1.7 µA. If the kit has a Deep Sleep current of 2.5 µA (typical), the WoT current is expected to be ~4.4 µA.

## Tuning procedure

<details><summary><b> Create a custom BSP for your board </b></summary>

1. Create a custom BSP for your board having any device, by following the steps given in [ModusToolbox&trade; BSP Assistant user guide](https://www.infineon.com/ModusToolboxBSPAssistant). This code example was created for the device "CY8C4046LQI-T452".

2. Open the *design.modus* file from the *{Application root directory}/bsps/TARGET_APP_\<BSP-NAME>/config/* folder obtained in the previous step and enable CAPSENSE&trade; to get the *design.cycapsense* file. CAPSENSE&trade; configuration can then be started from scratch as explained below.


</details>

The following steps explain the tuning procedure as shown in Figure 9. 

> **Note:** See the section "Selecting CAPSENSE&trade; hardware parameters" in the [PSoC&trade; 4 and PSoC&trade; 6 MCU CAPSENSE&trade; design guides](https://www.infineon.com/AN85951) to learn about the considerations for selecting each parameter value.

**Figure 9. CSD button widget tuning flow**  

<img src="images/tuning-flowchart.png" alt="" width="500" />

Do the following to tune the button widget:

- [Stage 1: Set the initial hardware parameters](#stage-1-set-the-initial-hardware-parameters)

- [Stage 2: Set the sense clock frequency](#stage-2-set-the-sense-clock-frequency)

- [Stage 3: Fine-tune for required SNR and refresh rate](#stage-3-fine-tune-for-required-snr-and-refresh-rate)

- [Stage 4: Tune the threshold parameters](#stage-4-tune-the-threshold-parameters)

### Stage 1: Set the initial hardware parameters
---------

1. Connect the board to your PC using the provided USB cable through the KitProg3 USB connector.
2. Launch the device configurator tool.

    Launch the device configurator in Eclipse IDE for ModusToolbox&trade; from the **Tools** section in the IDE **Quick Panel** or in Standalone mode from *{ModusToolbox&trade; install directory}/ModusToolbox/tools_{version}/device-configurator/device-configurator*. In this case, after opening the application, select **File** > **Open** and open the *design.modus* file of the respective application, which is present in the *{Application root directory}/bsps/TARGET_APP_\<BSP-NAME>/config/* folder.

3. In the PSoC&trade; [4000T](https://www.infineon.com/CY8CPROTO-040T) kit, the button pin is connected to CAPSENSE&trade; channel (MSCLP 0). Therefore, enable CAPSENSE&trade; channel in the device configurator as shown in Figure 10.

   **Figure 10. Enable MSCLP channels in Device Configurator**

   <img src="images/device-configurator.png" alt="" width="600"/>

      Save the changes and close the window.

4. Launch the CAPSENSE&trade; Configurator tool.
   
   You can launch the CAPSENSE&trade; Configurator tool in Eclipse IDE for ModusToolbox&trade; from the 'CAPSENSE&trade;' peripheral setting in the device configurator or directly from the **Tools** section in the IDE **Quick Panel**. You can also launch it in standalone mode from *{ModusToolbox&trade; install directory}/ModusToolbox/tools_{version}/capsense-configurator/capsense-configurator*. In this case, after opening the application, select **File** > **Open** and open the *design.cycapsense* file of the respective application, which is present in the *{Application root directory}/bsps/TARGET_APP_\<BSP-NAME>/config/* folder.

   See the [ModusToolbox&trade; CAPSENSE&trade; configurator tool guide](https://www.infineon.com/ModusToolboxCapSenseConfig) for step-by-step instructions on how to configure and launch CAPSENSE&trade; in ModusToolbox&trade;. 

5. In the **Basic** tab, note that the button widget 'Button0' is configured as a CSX-RM (mutual-cap) as shown in Figure 11.

   **Figure 11. CAPSENSE&trade; Configurator - Basic tab**

   <img src="images/basic-csd-settings.png" alt="" width="600"/>

   <br>

6. Go to **General** > **Advanced** tab and do the following as shown in Figure 12.
   <ol type="A">
   <li>

   Select **CAPSENSE&trade; IMO Clock frequency** as **46 MHz**. 
   </li>

   <li>

   Set the **Modulator clock divider** to **1** to obtain the maximum available modulator clock frequency.
   </li>

   <li>

   Set the **Number of init sub-conversions** based on the hint shown when you hover over the edit box. Retain the default value.
   </li>

   <li>

   Use **Wake-on-Touch settings** to set the refresh rate and frame timeout while in the lowest-power mode (Wake-on-Touch mode). Set **Wake-on-Touch scan interval (µs)** based on the required low-power state scan refresh rate. For example, to get a 16 Hz refresh rate, set the value to **62500**. 
   </li>


   <li>

   Set the **Number of frames in Wake-on-Touch** as the maximum number of frames to be scanned in WoT mode, if there is no touch detected. This determines the maximum time the device will be kept in the lowest-power mode if there is no user activity. Calculate the maximum time by multiplying this parameter with the **Wake-on-Touch scan interval (µs)** value.

   For example, to get 10 seconds as the maximum time in WoT mode, set the **Number of frames in Wake-on-Touch** to **160** for the  scan interval set as 62500 µs.

   > **Note:** For tuning low-power widgets, the **Number of frames in Wake-on-Touch** must be less than the  **Maximum number of raw counts in SRAM** based on the number of sensors in WoT mode as follows:

     **Table 2. Maximum number of raw counts in SRAM**

      Number of low <br> power widgets  | Maximum number of <br> raw counts in SRAM
      :---------------------| :-----
      1  | 245
      2  | 117
      3  | 74
      4  | 53
      5  | 40
      6  | 31
      7  | 25
      8  | 21
   
   **Figure 12. CAPSENSE&trade; Configurator – General settings**

   <img src="images/advanced-general-settings.png" alt="" width="550"/>

   </li>

   <br>

   <li>

    Retain the default settings for all regular and low-power widget filters. You can enable or update the filters later depending on the SNR requirements in [Stage 3: Fine-tune for required SNR and refresh rate](#stage-3-fine-tune-for-required-snr-and-refresh-rate).

    Filters reduce the peak-to-peak noise, and using software filters results in a higher scan time.
   

   > **Note:** Each tab has a **Restore Defaults** button to restore the parameters of that tab to their default values.

7. Go to the **CSD and CSX settings** tab and make the following changes as shown in Figure 13 and Figure 14.

   **Table 3. CSD and CSX Parameters**

   Parameters | CSD | CSX
     :---------|  :-------------|  :-----------  
   Inactive sensor connection | Shield | Ground
   Shield mode | Active |NA
   Total shield count  | 9 |NA
   Raw count calibration level | 70 | 40

 
   
   **Raw count calibration level(%)** helps in achieving the required CDAC calibration levels (85% of maximum count by default) for all sensors in the widget, while maintaining the same sensitivity across the sensor elements.
      This can be reduced, if the application reaches the saturation level on a touch event.
      
   **Figure 13. CAPSENSE&trade; Configurator - Advanced CSD settings**

   <img src="images/advanced-csd-settings.png" alt="" width="550"/>

   **Figure 14. CAPSENSE&trade; Configurator - Advanced CSX settings**

   <img src="images/advanced-csx-settings.png" alt="" width="550"/>

  
8. Go to **Advanced** > **Widget Details** tab. Select **Button0** from the left pane, and then set the following as shown in Figure 15.

   - **Sense clock divider:** Retain default value (will be set in [Stage 2](#stage-2-set-the-sense-clock-frequency))

   - **Clock source:** Direct

     > **Note:** Spread spectrum clock (SSC) or PRS clock can be used as a clock source to deal with EMI/EMC issues.

   - **Number of sub-conversions:** 60

     60 is a good starting point to ensure a fast scan time and sufficient signal. This value is adjusted as required in [Stage 3](#stage-3-fine-tune-for-required-snr-and-refresh-rate).
   - **Finger threshold:** 20

   - **Noise threshold:** 10

   - **Negative noise threshold:** 10

   - **Low-baseline reset:** 30

   - **Hysteresis:** 5

   - **ON debounce:** 3

      These values reduces the influence of baseline on the sensor signal, which helps to get the true difference-count. Retain the default values for the widget threshold parameters; these parameters are set in [Stage 4](#stage-4-tune-the-threshold-parameters).

     **Figure 15. CAPSENSE&trade; Configurator - Widget Details tab** 
      
     <img src="images/advanced-widget-settings.png" alt="" width="570" />

   <br>

9. Go to the **Scan Configuration** tab to select the pins, scan slots, and then do the following as shown in Figure 16.

   - Configure the pin for the electrode using the drop-down menu.

   - Configure the scan slot using the **Auto-Assign Slots** option or each sensor is allotted a scan slot based on the entered slot number. 

   - Check the notice list for warning or errors. 
   
   > **Note:** Enable the **Notice List** in the **View** menu if it is not visible.

      **Figure 16. Scan Configuration tab**

    <img src="images/scan-configuration.png" alt="" width="570"/>

   <br>

10. Click **Save** to apply the settings.

### Stage 2: Set the sense clock frequency
-----------
The sense clock is derived from the modulator clock using a clock-divider and is used to scan the sensor by driving the CAPSENSE&trade; switched capacitor circuits. Both the clock source and the clock divider are configurable. The sense clock divider should be configured such that the pulse width of the sense clock is long enough to allow the sensor capacitance to charge and discharge completely. This is verified by observing the charging and discharging waveforms of the sensor, using an oscilloscope and an active probe. The sensors should be probed close to the electrode, and not at the sense pins or the series resistor. 

See Figure 17 and Figure 18 for waveforms observed on the shield. Figure 17  shows proper charging when the sense clock frequency is correctly tuned. The minimum pulse width is 5Tau,  i.e., the voltage is reaching minimum 99.3% of the required voltage at the end of each phase. Figure 18 shows incomplete settling (charging/discharging).

  **Figure 17. Proper charge cycle of a sensor**

  <img src="images/sense_clock_valid.png" alt="Figure 21" width="550"/>


  **Figure 18. Improper charge cycle of a sensor**

  <img src="images/sense_clock_invalid.png" alt="Figure 22" width="550"/>

<br>

1. Program the board and launch thev CAPSENSE&trade; Tuner.

2. Observe the charging waveform of the sensor as described earlier. 

3. If the charging is incomplete, increase the **Sense clock divider**. Do this in CAPSENSE&trade; Tuner by selecting the sensor and editing the **Sense clock divider parameter** in the **Widget/Sensor Parameters** panel as shown in Figure 19.

   > **Note:** The sense clock divider should be **divisible by 2**. This ensures that two scan phases have equal durations. 

   After editing the value, click the **Apply to Device** button and observe the waveform again. Repeat this until complete settling is observed.  
   
4. Click the **Apply to Project** button to save the configuration to your project. 

   **Figure 19. Sense clock divider setting**

   <img src="images/sense_clock_divider_setting.png" alt="" width="350" />

   <br>
   

5. Repeat this process for all the sensors and the shield. Each sensor may require a different sense clock divider value to charge/discharge completely. But all the sensors that are in the same scan slot should have the same sense clock source, sense clock divider, and number of sub-conversions. Therefore, take the largest sense clock divider in a given scan slot and apply it to all the other sensors that share the slot.

### Stage 3: Fine-tune for required SNR and refresh rate
------------

To ensure reliable operation, the sensor should be tuned to have a minimum SNR of 5:1 and a minimum signal of 50. The sensitivity can be increased by increasing the number of sub-conversions and the noise can be decreased by enabling filters. 

> **Note:** If the sensor raw count saturates (equals Max Raw count) on touch, reduce the Raw count calibration level(%). which helps in avoiding saturation.

The steps for optimizing these parameters are as follows:

1. Measure the SNR as mentioned in the [Operation](#operation) section.

2. If the SNR is less than 5:1, increase the number of sub-conversions.  Edit the number of sub-conversions (N<sub>sub</sub>) directly in the **Widget/Sensor parameters** tab of the CAPSENSE&trade; Tuner.

   > **Note:** Number of sub-conversion should be greater than or equal to 8.

3.  Load the parameters to the device and measure SNR as mentioned in Steps 10 and 11 in the [Operation](#operation) section. 
   
      Repeat steps 1 to 3 until the following conditions are met:
      - Measured SNR from the previous stage is greater than 5:1
      - Signal count is greater than 50

4. If the system is very noisy (>40% of signal), enable filters.

   This example has the CIC2 filter enabled, which increases the resolution for the same scan time. See [AN234231 - Achieving lowest-power capacitive sensing with PSoC&trade; 4000T](https://www.infineon.com/dgdl/Infineon-AN234231_PSoC_4000T_Lowest_Power_CAPSENSE-ApplicationNotes-v06_00-EN.pdf?fileId=8ac78c8c8929aa4d0189f4a848e350bc) for detailed information on the CIC2 filter. Whenever CIC2 filter is enabled, it is recommended to enable the IIR filter for optimal noise reduction. Therefore, this example has the IIR filter enabled as well.
   <ol type="A">
   <li>

   Open **CAPSENSE&trade; Configurator** from ModusToolbox&trade; **Quick Panel** and select the appropriate filter as shown in Figure 20.

   **Figure 20. Filter settings in CAPSENSE&trade; Configurator**

   <img src="images/advanced-filter-settings.png" alt="" width="570"/>
   </li>
   
   <br>
   <li>

   Enable the filter based on the type of noise in your system. See [AN85951 – PSoC&trade; 4 and PSoC&trade; 6 MCU CAPSENSE&trade; design guide](https://www.infineon.com/AN85951) for more details.
   </li>
   <li>

   Click **Save** and close CAPSENSE&trade; Configurator. Program the device to update the filter settings.
   </li>

   > **Note** : Increasing the number of sub-conversions and enabling filters will increase the scan time which in turn decreases the responsiveness of the sensor. Increase in the scan time also increases power consumption. Therefore, the number of sub-conversions and filter configurations must be optimized to achieve a balance between SNR, power, and refresh rate.

### Stage 4: Tune the threshold parameters
-----------

Various thresholds, relative to the signal, need to be set for each sensor. Do the following in CAPSENSE&trade; Tuner to set up the thresholds for a widget:

1. Switch to the **Graph View** tab and select **Button0**.

2. Touch the sensor and monitor the touch signal in the **Sensor Signal** graph, as shown in Figure 21. 

   **Figure 21. Sensor signal when the sensor is touched**

   <img src="images/tuner-diff-signal.png" alt="" width="570"/>

   <br>

3. When the signal is measured, set the thresholds according to the following recommendations:

   - **Finger threshold =** 80% of the signal

   - **Noise threshold =** 40% of the signal

   - **Negative noise threshold** = 40% of the signal

   - **Hysteresis =** 10% of the signal

   - **Debounce =** 3 (Default)

4. Set the threshold parameters in the **Widget/Sensor Parameters** section of the CAPSENSE&trade; Tuner as shown in Figure 22.

   **Figure 22. Widget threshold parameters**

   <img src="images/tuner-threshold-settings.png" alt="" width="270"/>

   <br>

5. Click **Apply to Device** as shown in Figure 23 to apply the settings to the device and the project.

   **Figure 23. Apply settings to device**

   <img src="images/tuner-apply-settings-device.png" alt=""/>
   
   After applying the configuration, test the performance by touching the button. If your sensor is tuned correctly, you will observe the touch status go from 0 to 1 in the **Status** panel of the **Graph View** tab as shown in Figure 24. The status of the button is also indicated by  LED2 in the kit; LED2 turns ON when the finger touches the button and turns OFF when the finger is removed.


   **Figure 24. Sensor status in CAPSENSE&trade; Tuner**

   <img src="images/tuner-status.png" alt="" width="570"/>

   <br>

6. Click **Apply to Project** as shown in Figure 25. The change is updated in the *design.cycapsense* file. Close **CAPSENSE&trade; Tuner** and launch **CAPSENSE&trade; Configurator**. You should see all the changes made in the CAPSENSE&trade; Tuner are reflected in the **CAPSENSE&trade; Configurator**.

   **Figure 25. Apply settings to Project**

   <img src="images/tuner-apply-settings-project.png" alt="Figure 29"/>

   <br>

   Sensor tuning parameters obtained based on the [CY8CPROTO-040T](https://www.infineon.com/CY8CPROTO-040T), is shown in Table 4.

   **Table 4. Sensor tuning parameters obtained based on sense for CY8CPROTO-040T**
  
   Parameter | Button0 | LowPower0
   :------ | :------- | :-----
   Signal	|60	|526
   Finger threshold 	|48|420
   Noise threshold |24|210
   Negative noise threshold	|24|210
   Hysteresis	| 6 |NA
   ON debounce	|3|3
   Low baseline reset	|30|30

###  **Process time measurement**
--------------------


To set the optimum refresh rate of each power mode, measure the process time of the application.

Perform the following steps to measure the process time of the blocks in the application code while excluding the scan time:

1. Enable ENABLE_RUN_TIME_MEASUREMENT macro in *main.c* as follows:
      
      ```
      #define ENABLE_RUN_TIME_MEASUREMENT (1u)
      ```     
      This macro enables the system tick configuration and runtime measurement functionalities. 

2.	Place the start_runtime_measurement() function call before the application code and the stop_runtime_measurement() function call after it. The stop_runtime_measurement() function will return the execution time in microseconds(µs). 
 
      ```   
         #if ENABLE_RUN_TIME_MEASUREMENT
            uint32_t run_time = 0;
            start_runtime_measurement();
         #endif

         /* User Application Code Start */
         .
         .
         .
         /* User Application Code Stop */

         #if ENABLE_RUN_TIME_MEASUREMENT
            run_time = stop_runtime_measurement();
         #endif
      ```

3.	Run the application in Debug mode with breakpoints placed at the active_processing_time and alr_processing_time variables as follows:
      ```
         #if ENABLE_RUN_TIME_MEASUREMENT
            active_processing_time=stop_runtime_measurement();
         #endif
         and 
         #if ENABLE_RUN_TIME_MEASUREMENT
            alr_processing_time=stop_runtime_measurement();
         #endif
      ``` 
4. Read the variables by adding them into **Expressions view** tab.
5. Update related macros with earlier measured processing times in *main.c* as follows:
      ```
      #define ACTIVE_MODE_PROCESS_TIME     (xx)

      #define ALR_MODE_PROCESS_TIME        (xx)
      ```
### **Scan time Measurement**
--------------------
Scan time is necessary to calculate the refresh rate of the application power modes. The total scan time of all the widgets in this code example is 12 µs.

The scan time can be calculated as follows:

The scan time includes the MSCLP initialization time, Cmod, and the total sub-conversions of the sensor. 

To control the Cmod initialization sequence, set the "Enable coarse initialization bypass" configurator option as listed in Table 5.

**Table. 5 Enable coarse initialization bypass**
Enable coarse initialization bypass | Behaviour
:-------------|:---------
TRUE|Cmod initialization happens only once before scanning the sensors of the widget
FALSE| Cmod initialization happens before scanning each sensor of the widget

Use the following equations to measure the widgets scan time based on coarse initialization bypass options selected: 

**Equation 2. Scan time calculation of a widget with coarse initialization bypass enabled**

<img src="images/scan_time_equation_bypass_enabled.png" width=400/>

**Equation 3. Scan time calculation of a widget with coarse initialization bypass disabled**

<img src="images/scan_time_equation_bypass_disabled.png" width=400/>


where,

$n$ - Total number of sensors in the widget

$N_{init}$ - Number of init sub-conversions

$N_{sub}$ - Number of sub-conversions

$SnsClkDiv$ - Sense clock divider

$F_{mod}$ - Modulator clock frequency

$k$ - Measured Initialization time (MSCLP+Cmod).



The value of **$k$** measured for this application is ~9.865 µs. It remains constant for all widgets. 

**$k$** can be measured using oscilloscope, as shown in Figure 26.

**Figure 26. '$k$' value measurement**

   <img src="images/scantime_wave.png" alt="" width="570"/>

   <br>

Update the following macros in *main.c* using the calculated scan time. For this application, the value remains the same for both macros.

```
#define ACTIVE_MODE_FRAME_SCAN_TIME     (xx)

#define ALR_MODE_FRAME_SCAN_TIME        (xx)
```
<br>

> **Note :** If the application has more than one widget, add the scan time of individual widgets calculated.

<br>

## Debugging

You can debug this project to step through the code. In the IDE, use the **\<Application Name> Debug (KitProg3_MiniProg4)** configuration in the **Quick Panel**. For details, see the "Program and debug" section in the [Eclipse IDE for ModusToolbox&trade; user guide](https://www.infineon.com/MTBEclipseIDEUserGuide).

By default, the debug option is disabled in the device configurator. To enable the debug option, see the [Set up VDDA supply voltage and debug mode](#set-up-the-vdda-supply-voltage-and-debug-mode-in-device-configurator) section. To achieve low power consumption, it is recommended to disable it. 

<details><summary><b>In Eclipse IDE</b></summary>

Use the **\<Application Name> Debug (KitProg3_MiniProg4)** configuration in the **Quick Panel**. For details, see the "Program and debug" section in the [Eclipse IDE for ModusToolbox&trade; user guide](https://www.infineon.com/MTBEclipseIDEUserGuide).

</details>


<details><summary><b>In other IDEs</b></summary>

Follow the instructions in your preferred IDE.
</details>

## Design and implementation

The project contains a button widget configured in CSX-RM sensing mode. See the [Tuning procedure](#tuning-procedure) section for step-by-step instructions to configure the other settings of the **CAPSENSE&trade; Configurator**.

The project uses the [CAPSENSE&trade; middleware](https://github.com/Infineon/capsense) (see ModusToolbox&trade; user guide for more details on selecting a middleware). See [AN85951 - PSoC&trade; 4 and PSoC&trade; 6 MCU CAPSENSE&trade; design guide](https://www.infineon.com/AN85951) for more details on CAPSENSE&trade; features and usage.

The [ModusToolbox&trade;](https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software) provides a GUI-based tuner application for debugging and tuning the CAPSENSE&trade; system. The *CAPSENSE&trade; tuner* application works with EZI2C and UART communication interfaces. This project has an SCB block configured in EZI2C mode to establish communication with the on-board KitProg, which in turn enables reading the CAPSENSE&trade; raw data by the CAPSENSE&trade; tuner. See [EZI2C - Peripheral settings](#resources-and-settings).

The CAPSENSE&trade; data structure that contains the CAPSENSE&trade; raw data is exposed to the CAPSENSE&trade; Tuner by setting up the I2C communication data buffer with the CAPSENSE&trade; data structure. This enables the tuner to access the CAPSENSE&trade; raw data for tuning and debugging CAPSENSE&trade;.

The successful tuning of the button is indicated by an LED in the pioneer kit; the LED2 is turned ON when the finger touches the button and turned OFF when the finger is removed from the button.

### Set up the VDDA supply voltage and Debug mode in Device Configurator

1. Open **Device configurator** from the **Quick Panel**. 

2. Go to the **System** tab. Select the **Power** resource, and set the VDDA value under **Operating Conditions** as shown in Figure 27. 

   **Figure 27. Setting the VDDA supply in the System tab of device configurator**

   <img src="images/vdda-settings.png" alt="" width="600"/> 

3. By default, the Debug mode is disabled for this application to reduce power consumption. Enable the Debug mode to enable the SWD pins as shown in Figure 28.

   **Figure 28. Enable Debug mode in the System tab of Device Configurator**

   <img src="images/enable_debug.png" alt="" width="600"/>

### Resources and settings

The EZI2C configurations used for tuner communications are shown in Figure 29.
   
   **Figure 29. EZI2C settings**

   <img src="images/ezi2c-config.png" alt="" width="600"/>

<br>

**Table 6. Application resources**

 Resource  |  Alias/object     |    Purpose     
 :------- | :------------    | :------------ 
 SCB (EZI2C) (PDL) | CYBSP_EZI2C          | EZI2C slave driver to communicate with CAPSENSE&trade; Tuner 
 CAPSENSE&trade; | CYBSP_MSC | CAPSENSE&trade; driver to interact with the MSCLP hardware and interface the CAPSENSE&trade; sensors 
 Digital pin     | CYBSP_USER_LED2, CYBSP_USER_BTN | To show the button operation

</details> 

### Firmware flow

**Figure 30. Firmware flowchart**

<img src="images/firmware-flowchart.png" alt="" width="500"/>

<br>

## Related resources

Resources  | Links
-----------|----------------------------------
Application notes  | [AN79953](https://www.infineon.com/AN79953) - Getting started with PSoC&trade; 4 <br> [AN85951](https://www.infineon.com/AN85951) - PSoC&trade; 4 and PSoC&trade; 6 MCU CAPSENSE&trade; design guide <br> [AN234231](https://www.infineon.com/AN234231) - Achieving lowest-power capacitive sensing with PSoC&trade; 4000T
Code examples | [Using ModusToolbox&trade;](https://github.com/Infineon/Code-Examples-for-ModusToolbox-Software) on GitHub
Device documentation | [PSoC&trade; 4 datasheets](https://www.infineon.com/cms/en/search.html?intc=searchkwr-return#!view=downloads&term=psoc%204&doc_group=Data%20Sheet) <br>[PSoC&trade; 4 technical reference manuals](https://www.infineon.com/cms/en/search.html#!term=psoc%204%20technical%20reference%20manual&view=all)
Development kits | Select your kits from the [Evaluation board finder](https://www.infineon.com/cms/en/design-support/finder-selection-tools/product-finder/evaluation-board).
Libraries on GitHub  | [mtb-hal-cat2](https://github.com/Infineon/mtb-hal-cat2) - Hardware Abstraction Layer (HAL) library
Middleware on GitHub | [capsense](https://github.com/Infineon/capsense) - CAPSENSE&trade; library and documents <br>
Tools  | [ModusToolbox&trade;](https://www.infineon.com/modustoolbox) – ModusToolbox&trade; software is a collection of easy-to-use libraries and tools enabling rapid development with Infineon MCUs for applications ranging from wireless and cloud-connected systems, edge AI/ML, embedded sense and control, to wired USB connectivity using PSoC&trade; Industrial/IoT MCUs, AIROC&trade; Wi-Fi and Bluetooth&reg; connectivity devices, XMC&trade; Industrial MCUs, and EZ-USB&trade;/EZ-PD&trade; wired connectivity controllers. ModusToolbox&trade; incorporates a comprehensive set of BSPs, HAL, libraries, configuration tools, and provides support for industry-standard IDEs to fast-track your embedded application development.

<br>

## Other resources

Infineon provides a wealth of data at [www.infineon.com](https://www.infineon.com) to help you select the right device, and quickly and effectively integrate it into your design.

## Document history

Document title: *CE238820* - *PSoC&trade; 4: MSCLP low-power mutual-capacitance button*

 Version | Description of change
 ------- | ---------------------
 1.0.0   | New code example 
 2.0.0   | Major update to support ModusToolbox&trade; v3.2 and CAPSENSE&trade; Middleware v5.0. This version is not backward compatible with previous versions of ModusToolbox&trade; software.

<br>

All other trademarks or registered trademarks referenced herein are the property of their respective owners.  

The Bluetooth&reg; word mark and logos are registered trademarks owned by Bluetooth SIG, Inc., and any use of such marks by Infineon is under license.


---

© Cypress Semiconductor Corporation, 2023. This document is the property of Cypress Semiconductor Corporation, an Infineon Technologies company, and its affiliates ("Cypress").  This document, including any software or firmware included or referenced in this document ("Software"), is owned by Cypress under the intellectual property laws and treaties of the United States and other countries worldwide.  Cypress reserves all rights under such laws and treaties and does not, except as specifically stated in this paragraph, grant any license under its patents, copyrights, trademarks, or other intellectual property rights.  If the Software is not accompanied by a license agreement and you do not otherwise have a written agreement with Cypress governing the use of the Software, then Cypress hereby grants you a personal, non-exclusive, nontransferable license (without the right to sublicense) (1) under its copyright rights in the Software (a) for Software provided in source code form, to modify and reproduce the Software solely for use with Cypress hardware products, only internally within your organization, and (b) to distribute the Software in binary code form externally to end users (either directly or indirectly through resellers and distributors), solely for use on Cypress hardware product units, and (2) under those claims of Cypress's patents that are infringed by the Software (as provided by Cypress, unmodified) to make, use, distribute, and import the Software solely for use with Cypress hardware products.  Any other use, reproduction, modification, translation, or compilation of the Software is prohibited.
<br>
TO THE EXTENT PERMITTED BY APPLICABLE LAW, CYPRESS MAKES NO WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, WITH REGARD TO THIS DOCUMENT OR ANY SOFTWARE OR ACCOMPANYING HARDWARE, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.  No computing device can be absolutely secure.  Therefore, despite security measures implemented in Cypress hardware or software products, Cypress shall have no liability arising out of any security breach, such as unauthorized access to or use of a Cypress product. CYPRESS DOES NOT REPRESENT, WARRANT, OR GUARANTEE THAT CYPRESS PRODUCTS, OR SYSTEMS CREATED USING CYPRESS PRODUCTS, WILL BE FREE FROM CORRUPTION, ATTACK, VIRUSES, INTERFERENCE, HACKING, DATA LOSS OR THEFT, OR OTHER SECURITY INTRUSION (collectively, "Security Breach").  Cypress disclaims any liability relating to any Security Breach, and you shall and hereby do release Cypress from any claim, damage, or other liability arising from any Security Breach.  In addition, the products described in these materials may contain design defects or errors known as errata which may cause the product to deviate from published specifications. To the extent permitted by applicable law, Cypress reserves the right to make changes to this document without further notice. Cypress does not assume any liability arising out of the application or use of any product or circuit described in this document. Any information provided in this document, including any sample design information or programming code, is provided only for reference purposes.  It is the responsibility of the user of this document to properly design, program, and test the functionality and safety of any application made of this information and any resulting product.  "High-Risk Device" means any device or system whose failure could cause personal injury, death, or property damage.  Examples of High-Risk Devices are weapons, nuclear installations, surgical implants, and other medical devices.  "Critical Component" means any component of a High-Risk Device whose failure to perform can be reasonably expected to cause, directly or indirectly, the failure of the High-Risk Device, or to affect its safety or effectiveness.  Cypress is not liable, in whole or in part, and you shall and hereby do release Cypress from any claim, damage, or other liability arising from any use of a Cypress product as a Critical Component in a High-Risk Device. You shall indemnify and hold Cypress, including its affiliates, and its directors, officers, employees, agents, distributors, and assigns harmless from and against all claims, costs, damages, and expenses, arising out of any claim, including claims for product liability, personal injury or death, or property damage arising from any use of a Cypress product as a Critical Component in a High-Risk Device. Cypress products are not intended or authorized for use as a Critical Component in any High-Risk Device except to the limited extent that (i) Cypress's published data sheet for the product explicitly states Cypress has qualified the product for use in a specific High-Risk Device, or (ii) Cypress has given you advance written authorization to use the product as a Critical Component in the specific High-Risk Device and you have signed a separate indemnification agreement.
<br>
Cypress, the Cypress logo, and combinations thereof, ModusToolbox, PSoC, CAPSENSE, EZ-USB, F-RAM, and TRAVEO are trademarks or registered trademarks of Cypress or a subsidiary of Cypress in the United States or in other countries. For a more complete list of Cypress trademarks, visit  [www.infineon.com](https://www.infineon.com) Other names and brands may be claimed as property of their respective owners. 
