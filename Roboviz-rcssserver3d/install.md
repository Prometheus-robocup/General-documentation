### Installing Packages for RoboCup Simulation 3D on xUbuntu 22.04

To set up the necessary packages for participating in the RoboCup simulation 3D, follow these steps:

```bash
echo 'deb http://download.opensuse.org/repositories/science:/SimSpark/xUbuntu_22.04/ /' | sudo tee /etc/apt/sources.list.d/science:SimSpark.list
```

```bash
curl -fsSL https://download.opensuse.org/repositories/science:SimSpark/xUbuntu_22.04/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/science_SimSpark.gpg > /dev/null
```

```bash
sudo apt update
```

```bash
sudo apt install rcssserver3d
```

### Installing RoboViz

To install RoboViz, you need Java 17 and Gradle. Follow these comprehensive instructions to ensure all dependencies are properly installed.

#### Install Java 17

```bash
sudo apt update
sudo apt install openjdk-17-jdk
```

#### Install Gradle

First, install the required dependencies:

```bash
sudo apt install wget unzip
```

Download and install Gradle:

```bash
wget https://services.gradle.org/distributions/gradle-7.5-bin.zip -P /tmp
sudo unzip -d /opt/gradle /tmp/gradle-7.5-bin.zip
```

Set up the environment variables:

```bash
sudo nano /etc/profile.d/gradle.sh
```

Add the following lines to the file:

```bash
export GRADLE_HOME=/opt/gradle/gradle-7.5
export PATH=${GRADLE_HOME}/bin:${PATH}
```

Make the script executable:

```bash
sudo chmod +x /etc/profile.d/gradle.sh
```

Load the new environment variables:

```bash
source /etc/profile.d/gradle.sh
```

Verify the installation:

```bash
gradle -v
```

#### Download and Build RoboViz

Clone the RoboViz repository:

```bash
git clone https://github.com/magmaOffenburg/RoboViz.git
cd RoboViz
```

Build RoboViz:

```bash
./scripts/build.sh
```

#### Run RoboViz

After building, you can run RoboViz using:

```bash
./bin/roboviz.sh
```

For more information and pre-built binaries for Windows, Linux, and Mac, you can visit the [RoboViz GitHub repository](https://github.com/magmaOffenburg/RoboViz).
