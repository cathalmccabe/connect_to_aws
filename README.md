# Xilinx ICS 2020 tutorial

Monday 29 June 2020 10:00 - 18:00 (Central European Time)

## Connecting to AWS

This  guide will show you how to connect to a Xilinx provided AWS EC2 F1 instance, and starting and stopping the instance. 

## Steps
Each registered participant to the tutorial has been allocated a pre-configured EC2 F1 instance. You should already have received an email with the following details:  

- Account ID,
- IAM username,
- Link to access a pre-configured EC2 F1 instance

### Login into the AWS and starting an F1 instance

* Follow the link provided by your instructor, or go to [https://console.aws.amazon.com/ec2](https://console.aws.amazon.com/ec2) to open a login page.

  If you see the "Root user sign in" prompt, asking for your e-mail and password, select **Sign in to a different account**

  You should see a login page similar to shown here:

  ![](images/connecting_lab/FigConnectingLab-1.png)

* For the *Account ID or Alias* enter `xilinx-aws-f1-developer-labs`  

  Use the username assigned to you by e-mail and enter the password provided by the instructors. Only use this username to log in to the AWS console. Later you will use **centos** as the username to login to the AWS instance.   

## Check the AWS region

* In the top right corner, using the drop-down button, make sure **N. Virginia (US East)** is selected. 

  ![](images/connecting_lab/FigConnectingLab-3.png)

  If you select the wrong region you may not see your instance

## Launch the instance

* Click on the **EC2** link on the dashboard, or if not visible, click on the _Services_ drop-down button and then click on **EC2**

  ![](images/connecting_lab/FigConnectingLab-4-1.png)
  ![](images/connecting_lab/FigConnectingLab-4-2.png)

* Click on the **Instances** link on the left panel

  ![](images/connecting_lab/FigConnectingLab-5.png)

  You may see several instances

* Enter your username in the filter field just below the **Launch Instance** button and hit enter

  ![](images/connecting_lab/FigConnectingLab-6.png)

* Making sure that your instance is selected, click on the **Actions > Instance State > Start**

  ![](images/connecting_lab/FigConnectingLab-7.png)

* Wait for a few seconds, and click on the refresh button(![alt tag](./images/Fig-refresh.png)) to see the updated status. Repeat this until you see the instance is *running*. It usually takes about 20-30 seconds for an instance to start. 

  ![](images/connecting_lab/FigConnectingLab-8.png)

9. Copy or note the IPv4 Public IP address. If you hover the mouse near the end of the IP address, you can click a button to copy 

  ![](images/connecting_lab/FigConnectingLab-9.png)



## Connect to instance

At this point you have several options to connect to your AWS instance. E.g. NICE DCV, RDP,  for remote desktop, PuTTY and similar for command line interface.

We recommend you first try to use Nice DCV to connect to your instance. This seems to work well on all operating systems. 

### Connecting to AWS instance using NICE DCV

NICE DCV as recommended by Amazon will be used to remote desktop to the instance.

* Download and install the appropriate NICE DCV client if necessary from here: https://download.nice-dcv.com

The NICE DCV session has already been started on the instance provided. .

#### Start NICE DCV

* Open the NICE DCV application, enter (or paste) the *IPv4 Public IP* from the Amazon console and click **Open**

  ![](./images/nice_dcv.png)

* When prompted, enter **centos** as the *username* and same password provided by your instructor 

  ![](./images/nice_dcv_desktop.png)

## Lab setup

* Open a terminal and execute the following commands to clone the *aws-fpga* repository and setup the Xilinx tools. aws-fpga includes the AWS F1 tools, HDK and documentation:

```sh
    git clone https://github.com/aws/aws-fpga $AWS_FPGA_REPO_DIR -b v1.4.14
    #Include AWS platforms by default
    echo "export PLATFORM_REPO_PATHS=$AWS_FPGA_REPO_DIR/Vitis/aws_platform/xilinx_aws-vu9p-f1_shell-v04261818_201920_2/" >> ~/.bashrc
    #Source XRT everytime a new terminal is open
    echo "source /opt/xilinx/xrt/setup.sh" >> ~/.bashrc
    #Reload .bashrc in the current terminal
    source ~/.bashrc
    #Source AWS configuration files
    source $AWS_FPGA_REPO_DIR/vitis_setup.sh
    source $AWS_FPGA_REPO_DIR/vitis_runtime_setup.sh
```

# Video Guide

You can also follow these short video guides to get connected:

Start AWS instance: https://www.youtube.com/watch?v=--o7PTRlePA&t=6s

Connect using NICE DCV: https://www.youtube.com/watch?v=7k6dG8hjKR0


## Start the labs

Once you have done this, open the tutorial instructions:

​	~/compute_acceleration/**ICS2020.html** 

Start from the first lab: **Introduction to Vitis Part 1**. 



## Appendix

## Nice DCV alternatives

You can use RDP (Windows), Microsoft *Remote Desktop* for Mac, Vinagre, Remmina (Linux), but the instructors will be limited on how much support they can give for these alternatives. 

For Microsoft *Remote Desktop* for Mac you must use this specific version: v8.0.43 as this has color depth settings. 

Where your client has the option, you need top set the color depth to 24-bit. 

### Connect using RDP

You can communicate with the instance using command line through PuTTY or Git Bash, and using GUI through remote desktop (RDP) connection.

1. Start a remote desktop session

1. Enter the *IPv4* address

1. Click on the **Show Options**

  ![](./images/connecting_lab/FigConnectingLab-10.png)

4. Select the **Display** tab and select *True Color (24 bit)* and click **Connect**

  ![](./images/connecting_lab/FigConnectingLab-11.png)

5. A certificate warning will be displayed. Click **Yes** to open the RDP session

6. Enter **centos** as the username and enter the provided password and click **OK**

  ![](./images/connecting_lab/FigConnectingLab-12.png)

Connect to AWS with RDP video guide:  https://www.youtube.com/watch?v=LBJaAiKtK-U

