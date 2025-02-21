### Unicorn BCI Core Recorder

Unicorn BCI Core Recorder is an application used to acquire, visualize and record data from Unicorn BCI Core devices. Unicorn BCI Core Recorder allows you to process raw EEG with pre-defined Notch and Bandpass filters. Recorded data can be stored in a CSV or BDF files. You can also stream data to external applications via LSL or UDP.

[Installing Unicorn BCI Core Recorder](#installing-unicorn-bci-core-recorder)<br/>
[Application](#application)<br/>
&nbsp;&nbsp;&nbsp;[Connecting to a device](#connecting-to-a-device)<br/>
&nbsp;&nbsp;&nbsp;[Control bar](#control-bar)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Start/Stop acquisition](#1-startstop-acquisition)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Record](#2-record)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Settings](#3-settings)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Acquisition settings](#acquisition-settings)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Recording settings](#recording-settings)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CSV file format](#csv-file-format)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[BDF file format](#bdf-file-format)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Network settings](#network-settings)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Receiving triggers via UDP](#receiving-triggers-via-udp)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Sending data via LSL](#sending-data-via-lsl)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Sending data via UDP](#sending-data-via-udp)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Device settings](#device-settings)<br/>
&nbsp;&nbsp;&nbsp;[Processing and display settings](#processing-and-display-settings)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Amplitude range](#amplitude-range)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Filters](#filters)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Notch](#notch)<br/>
&nbsp;&nbsp;&nbsp;[Scope](#scope)<br/>
&nbsp;&nbsp;&nbsp;[Signal quality indicators](#signal-quality-indicators)<br/>
[Using Unicorn BCI Core Recorder for a research experiment](#using-unicorn-bci-core-recorder-for-a-research-experiment)<br/>

## Installing Unicorn BCI Core Recorder

Unicorn BCI Core Recorder is delivered with g.tec Suite 2024. Ensure that you've installed g.tec Suite 2024 - 1.24.01 or later and the latest update. 'Unicorn BCI Core Recorder' is listed in the Applications section.

<p align="center">
<img src="./img/rec1.png" alt="drawing" width="500"/><br/>
</p>

## Application

<p align="center">
<img src="./img/rec3.png" alt="drawing" width="500"/><br/>
</p>

### Connecting to a device

The Connection dialog is displayed after opening 'Unicorn BCI Core Recorder'. Turn your device on and wait until the device is discovered. Select the device and click the 'Connect' button.

<p align="center">
<img src="./img/rec2.png" alt="drawing" width="500"/><br/>
</p>

### Control bar
<p align="center">
<img src="./img/rec4.png" alt="drawing" width="800"/><br/>
</p>

### 1. Start/Stop acquisition

This button initiates or halts data acquisition. The play button is visible when the device is connected and data acquisition is not active. Press the play button to initiate data acquisition. Data will be displayed after the play button was clicked. The stop button is visible if a data acquisition or recording session is currently active. To terminate a running data acquisition or recording session, press the stop button.

### 2. Record

This button initiates or halts data recording.

### 3. Settings

The settings dialog allows to configure acquisition, recording, network and device settings. To exit the settings dialog simply click the settings button again. 

### Acquisition settings

<p align="center">
<img src="./img/rec5.png" alt="drawing" width="500"/><br/>
</p>

Acquisition parameters can be modified in the acquisition dialog. It is possible to include or exclude Battery Level, Counter, Validation Indicator, Timing or Saturation Flags from data acquisition. Included signals will be written to files and network streams if enabled. 

The default order is:

Ch. 1 - EEG 1 - EEG channel 1 in microvolts<br/>
Ch. 2 - EEG 2 - EEG channel 2 in microvolts<br/>
Ch. 3 - EEG 3 - EEG channel 3 in microvolts<br/>
Ch. 4 - EEG 4 - EEG channel 4 in microvolts<br/>
Ch. 5 - EEG 5 - EEG channel 5 in microvolts<br/>
Ch. 6 - EEG 6 - EEG channel 6 in microvolts<br/>
Ch. 7 - EEG 7 - EEG channel 7 in microvolts<br/>
Ch. 8 - EEG 8 - EEG channel 8 in microvolts<br/>
Ch. 9 - SAT - Saturation flags<br/>
Ch. 10 - CNT - Counter<br/>
Ch. 11 - BAT - Battery Level in percent<br/>
Ch. 12 - VALID - Validation Indicator<br/>
Ch. 13 - DT - Delta time / Timespan between two received samples in milliseconds<br/>
Ch. 14 - STATUS - Status / Trigger Value<br/>

### Recording settings

Data can be stored in BDF or CSV file format. It is possible to select the recording format in the 'Recording' settings. 'Folder path' and 'File prefix' can be modified as well. It is possible to record raw data and processed data. Raw data and processed data can be enabled and disabled in the 'Recording' settings. Processed data means that the filtered which were selected are applied to the EEG data.

The default 'Folder path' is set to:

```C:\Users\<username>\Documents\gtec\Unicorn\BCI Core\Unicorn BCI Core Recorder```
 
and the 'File prefix' is set to 'UnicornRecorder'

<p align="center">
<img src="./img/rec6.png" alt="drawing" width="500"/><br/>
</p>

#### CSV file format

 Data is stored in serialized, comma-seperated format, if CSV logging is enabled. The number of columns depend on configuration defined in the [Acquisition Settings](#acquisition-settings)..

<p align="center">
<img src="./img/rec9.png" alt="drawing" width="700"/><br/>
</p>

#### Loading CSV files in Matlab

An import script is provided to read the Unicorn BCI Core Recorder file into Matlab. Open Matlab and select “Set Path”. 

Add the folder:

```C:\Users\<username>\Documents\gtec\Unicorn\BCI Core\Unicorn BCI Core Recorder\MATLAB Tools```

 to the Matlab search path and click save.

```Matlab
[datastruct] = unicornrecorder_read(filename)
```
Imports a Unicorn BCI Core Recorder data file and returns data, as well as recording information.

- Parameters:<br>
filename - String containing the name of file to import.
- Return:<br>
Matlab structure containing all information stored in the Unicorn BCI Core Recorder data file.
- Remarks:<br>
Type “help unicornrecorder_read” into the Matlab command window for further information.<br>
Example usage:<br>
data = unicornrecorder_read('UnicornRecorder_20190122_220912.csv');

#### BDF file format

Data is stored in the BDF+ file format if BDF logging is enabled. Data can be loaded from applications supporting BDF file format like EDFBrowser. The number of signals depend on configuration defined in the [Acquisition Settings](#acquisition-settings).

<p align="center">
<img src="./img/rec10.png" alt="drawing" width="700"/><br/>
</p>

### Network settings

Unicorn BCI Core Recorder features multiple network interfaces for sending triggers from an external application to Unicorn BCI Core Recorder or data from Unicorn BCI Core Recorder to an external application.

<p align="center">
<img src="./img/rec7.png" alt="drawing" width="500"/><br/>
</p>

#### Receiving triggers via UDP

Triggers can be sent from an external application like a stimulus presentation tool via UDP

IP and Port can be modified. The default ip is set to the ```127.0.0.1```. The default port is set to `1000`. The port must differ from the port used for receiving triggers.

<p align="center">
<img src="./img/rec13.png" alt="drawing" width="500"/><br/>
</p>

##### C# example

A C# example showing how to receive data from an external application is installed with Unicorn BCI Core Recorder. 

The example is installed to 

```C:\Users\<username>\Documents\gtec\Unicorn\BCI Core\Unicorn BCI Core Recorder\Examples\UDP Trigger Sender```

<p align="center">
<img src="./img/rec14.png" alt="drawing" width="500"/><br/>
</p>

##### Code snippets

These exsamples show how to send triggers from an external application to Unicorn BCI Core Recorder. The trigger value must be sent as a as ASCII character via UDP in order to be received properly.

This C# example can be modified and integrated into an application:

```C#
//Initialize socket
socket = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);
socket.EnableBroadcast = true;
endPoint = new IPEndPoint(IPAddress.Parse("127.0.0.1"), 1000);
socket.Connect(endPoint);

//Send trigger
byte[] sendBytes = Encoding.ASCII.GetBytes("1");
socket.SendTo(sendBytes, endPoint);
```

This Python example can be modified and integrated into an application:

```Python
import socket

# Initialize socket
socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
endPoint = ("127.0.0.1", 1000)

# Send trigger
sendBytes = b"1"
socket.sendto(sendBytes, endPoint)
```

##### Example: Using keystrokes as triggers

This example shows how to use keystrokes as trigger for Unicorn BCI Core Recorder.

```Python
import keyboard
import socket

def on_key_event(event):
    if event.event_type == keyboard.KEY_DOWN:
        sendBytes = ''
        if event.name == 'a':
            # Send trigger
            sendBytes = b"1"
        elif event.name == 's':
            # Send trigger
            sendBytes = b"2"

        #add your keys/triggers here

        if len(sendBytes)>0:
            print('Key: ' + event.name + ' Sending: ' + str(sendBytes))
            socket.sendto(sendBytes, endPoint)

# Initialize socket
socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
endPoint = ("127.0.0.1", 1000)

keyboard.on_press(on_key_event)
keyboard.wait('esc')
```

#### Sending data via LSL

It is possible to send data from Unicorn BCI Core Recorder to an external application using LSL.

It is possible to modify the LSL streamname. The default streamname is set to ```UnicornRecorderLSLStream```.

##### C# example

A C# example showing how to receive data from Unicorn BCI Core Recorder in C# via LSL.

The example is installed to 

```C:\Users\<username>\Documents\gtec\Unicorn\BCI Core\Unicorn BCI Core Recorder\Examples\LSL Receiver```

<p align="center">
<img src="./img/rec17.png" alt="drawing" width="500"/><br/>
</p>

#### Sending data via UDP

It is possible to send data from Unicorn BCI Core Recorder to an external application using UDP.

IP and Port can be modified. The default ip is set to the ```127.0.0.1```. The default port is set to `1001`. The port must differ from the port used for receiving triggers.

##### C# example

A C# example showing how to receive data from Unicorn BCI Core Recorder in C# via UDP.

The example is installed to 

```C:\Users\<username>\Documents\gtec\Unicorn\BCI Core\Unicorn BCI Core Recorder\Examples\UDP Receiver```

<p align="center">
<img src="./img/rec18.png" alt="drawing" width="500"/><br/>
</p>

#### Device settings

Device information can be read in the device dialog. The serial number and software versions of the Unicorn Brain Interface currently used are displayed in this dialog. Additionally, the digital outputs can be controlled within this dialog.

<p align="center">
<img src="./img/rec8.png" alt="drawing" width="500"/><br/>
</p>

### Processing and display settings

It is possible to modify signal processing and data visualization using this toolbar. Data recordings and network interfaces are restarted if filters are reconfigured during data acquisition.

<p align="center">
<img src="./img/rec16.png" alt="drawing" width="700"/><br/>
</p>

#### Amplitude range
The amplitude range changes the displayed amplitude range of all EEG channels in the [Data Viewer](#data-viewer). 

#### Filters

The 'Filter' box allows you to apply predefined IIR filters to the raw data to extract specified frequency bands and remove artifacts. Predefined filters settings are:

- 0.1 – 30 Hz Bandpass
- 0.1 – 50 Hz Bandpass
- 0.5 – 30 Hz Bandpass
- 0.5 – 50 Hz Bandpass
- 1 – 30 Hz Bandpass
- 1 – 50 Hz Bandpass
- 2 – 30 Hz Bandpass
- 2 – 50 Hz Bandpass
-  &#62; 0.1 Hz Highpass
-  &#62; 0.5 Hz Highpass
-  &#62; 1 Hz Highpass
-  &#62;  2 Hz Highpass
-  &#60; 20 Hz Lowpass
-  &#60; 50 Hz Lowpass
- None - No filter applied

#### Notch

The 'Notch' box allows you to apply predefined IIR filters to the raw data to remove power line hum from data.

- 50 Hz 
- 60 Hz 
- 50 & 60 Hz 
- Cascading 50 Hz - removes 50 Hz and multiples
- Cascading 60 Hz - removes 60 Hz and multiples
- Cascading 50 & 60 Hz  - removes 50, 60 Hz and multiples
- None - No filter applied

### Data viewer
<p align="center">
<img src="./img/rec12.png" alt="drawing" width="500"/><br/>
</p>

he Data Viewer displays incoming data in real-time.  All channels provided by the Unicorn are listed underneath. The data viewer is limited to a time range of 10 seconds. 

### Signal quality indicators

<p align="center">
<img src="./img/rec11.png" alt="drawing" width="150"/><br/>
</p>

The signal quality indicators provide feedback about the signal quality. Therefore, the raw EEG is filtered to a certain frequency range where amplitude variations are observed. It takes about 30 seconds until the filters have stabilized and the signal quality scope is reliable. If Unicorn BCI Core Electrodes are not setteling in the expected amplitude range, electrodes turn red, indicating bad signal quality. All Unicorn BCI Core Electrodes should turn green if the EEG amplitude stays in a proper range.

## Using Unicorn BCI Core Recorder for a research experiment

This image illustrates a typical use case for BCI research. It shows the capability to send a trigger from an external stimulus presentation framework to 'Unicorn BCI Core Recorder', synchronizing the trigger with the data captured by 'Unicorn BCI Core Recorder' ([Receiving triggers via UDP](#receiving-triggers-via-udp)). Both the data and trigger can then be transmitted to an external application using network outputs for real-time processing ([Network Settings](#network-settings)) using [UDP](#sending-data-via-udp) or [LSL](#sending-data-via-lsl). Additionally, the trigger and data can be processed offline from the BDF or CSV recordings ([Record Settings](#recording-settings)).

<p align="center">
<img src="./img/rec15.png" alt="drawing"/><br/>
</p>