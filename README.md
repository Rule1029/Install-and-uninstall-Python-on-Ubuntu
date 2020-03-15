# Install-and-uninstall-Python-on-Ubuntu

  ## Install Python
    
  ### 1.Update resource:
  ```
  # sudo apt update
  # sudo apt upgrade -y
  ```    

  ### 2.Install all the dependency package:
  ```
  # sudo apt install build-essential -y
  # sudo apt install libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev -y
  ```


  ### 3.Download the python installation package and unzip it:
  ```
  # wget https://www.python.org/ftp/python/3.7.1/Python-3.7.1.tgz
  # tar -xzvf Python-3.7.1.tgz
  ```

  ### 4.Configuration:
  ```
  # cd Python-3.7.1
  # ./configure --prefix=/opt/ptyhon3.7
  # ./configure --enable-optimizations
  ```
  The last command gonna optimize the binary file in order to run it faster, but it will run many test code and will cost half an hour(you can just skip this step).
  
  If an error occurs like this:
  ```
  zipimport.ZipImportError: can’t decompress data
  ```
  It means missing some denpendency package of zlib, then we can do this:
   - Install the package:
   ```
   #sudo apt-get -y install zlib*
   ```
   - Enter python installation package, and edit the file "Setup"(or "setup", "Setup.dist") under the path "Modules":
   ```
   # vim modules/setup 
   ```
   - find this line and uncomment it:
   ```
   #zlib zlibmodule.c -I$(prefix)/include -L$(exec_prefix)/lib -lz
   ```

  ### 5.Complie and install python:
  ```
  # sudo make
  # sudo make install
  ```

  ### 6.Update pip:
  ```
  # pip3 install --upgrade pip
  ```
  
  ### 7.Refresh system source:
  ```
  # source ~/.bashrc
  ```
  
  ### 8.Check:
  ```
  # Python3 -V
  ```
  
  ## Uninstall Python:
  
  ### 1.Use the commands below:
  ```
  # sudo apt-get remove python3
  # sudo apt-get update
  ```
  
  ### 2.Clean remains:
  use `whereis python` `whereis python3` to find all the remianing files, and remove all of them.
  
