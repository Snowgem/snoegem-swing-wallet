# Desktop GUI Wallet for [Snowgem](https://snowgem.org/)[®](#disclaimer)

## Graphical user interface wrapper for the [Snowgem](https://snowgem.org/)[®](#disclaimer) command line tools

This program provides a Graphical User Interface (GUI) for the Snowgem client tools that acts as a wrapper and 
presents the information in a user-friendly manner.

Before installing the Desktop GUI Wallet you need to have Snowgem up and running.
The snowgem binary and snowgem prams is avaiable [here](https://github.com/Snowgem/snowgem-swing-wallet/releases)

The following video also explains how to [set up the GUI wallet](https://www.youtube.com/watch?v=IDifG4h1bgE). 


1. Operating system and tools

   The Linux tools you need to build and run the Wallet GUI are Git, Java (JDK7 or later) and
   Ant. If using Ubuntu Linux, they may be installed via command: 
   ```
   user@ubuntu:~/build-dir$ sudo apt-get install git default-jdk ant
   ``` 
   For RedHat/CentOS/Fedora-type Linux systems the command is (like):
   ```
   user@centos:~/build-dir$ sudo yum install java-1.8.0-openjdk git ant 
   ```
   The name of the JDK package (`java-1.8.0-openjdk`) may vary depending on the Linux system, so you need to
   check it, if name `java-1.8.0-openjdk` is not accepted.
   If you have some other Linux distribution, please check your relevant documentation on installing Git, 
   JDK and Ant. The commands `git`, `java`, `javac` and `ant` need to be startable from command line 
   before proceeding with build.

2. Installing the built Snowgem GUI wallet

   Downloade the [Snowgem Binary distribution](https://github.com/Snowgem/snowgem-swing-wallet/releases):

   Assuming you have already downloaded the file `snowgem-1.0.x-linux64.tar.gz` which contains the command 
   line tools `snowgem-cli` and `snowgemd` and after decompressing it they are in a directory like 
   `/home/user/snowgem-1.0.x/bin/` move `./build/jars/SnowgemSwingWalletUI.jar` to directory `/home/user/snowgem-1.0.x/bin/`
   (the same dir. that contains `snowgem-cli` and `snowgemd`). 
   Example copy command:
   ```
   user@ubuntu:~/build-dir/snowgem-swing-wallet-ui$ cp ./build/jars/SnowgemSwingWalletUI.jar /home/user/snowgem-1.0.8/bin/    
   ```

3. Running the installed Snowgem GUI wallet

   Before running the GUI you need to start snowgemd (e.g. `snowgemd --daemon`). The wallet GUI is a Java program packaged 
   as an executable JAR file. It may be run from command line or started from another GUI tool (e.g. file manager). 
   Assuming you have already installed [Snowgem](https://github.com/Snowgem/snowgem-swing-wallet/releases) and the GUI Wallet
  `SnowgemSwingWalletUI.jar` in directory `/home/user/snowgem/src` one way to run it from command line is:
   ```
   user@ubuntu:~/build-dir/snowgem-swing-wallet-ui$ java -jar /home/user/snowgem/src/SnowgemSwingWalletUI.jar
   ```
   If you are using Ubuntu (or similar ;) Linux you may instead just use the file manager and 
   right-click on the `SnowgemSwingWalletUI.jar` file and choose the option "Open with OpenJDK 8 Runtime". 
   This will start the Snowgem GUI wallet.

### License
This program is distributed under an [MIT License](https://github.com/vaklinov/snowgem-swing-wallet-ui/raw/master/LICENSE).

### Disclaimer
[Zerocoin Electric Coin Company](https://trademarks.justia.com/owners/zerocoin-electric-coin-company-3232749/).

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

### Known issues and limitations

1. Issue: Wallet versions 0.58 and below, when running on systems with (typically non-western) locales that
redefine the decimal point in the OS locale settings, have problems with updating the GUI wallet state. 
A workaround is to change the [locale settings](https://windows.lbl.gov/software/optics/5-1-2/Optics4.jpg) to have dot as decimal separator.
1. Limitation: Wallet encryption has been temporarily disabled in Snowgem due to stability problems. A corresponding issue 
[#1552](https://github.com/snowgem/snowgem/issues/1552) has been opened by the Snowgem developers. Correspondingly
wallet encryption has been temporarily disabled in the Snowgem Desktop GUI Wallet.
1. Issue: the GUI wallet does not work correctly if snowgemd is started with a custom data directory, like:
`snowgemd -datadir=/home/data/whatever` This will be fixed in later versions.
1. Issue: GUI data tables (transactions/addresses etc.) allow copying of data via double click but also allow editing. 
The latter needs to be disabled. 
1. Limitation: The list of transactions does not show all outgoing ones (specifically outgoing Z address 
transactions). A corresponding issue [#1438](https://github.com/snowgem/snowgem/issues/1438) has been opened 
for the Snowgem developers. 
1. Limitation: The CPU percentage shown to be taken by snowgemd on Linux is the average for the entire lifetime 
of the process. This is not very useful. This will be improved in future versions.
