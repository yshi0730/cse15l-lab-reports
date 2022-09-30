Tutorial of logging into a course-specific account on ieng6.
---
* Installing Visual Studio Code

  1. Visit VScode website and [Install VScode](https://code.visualstudio.com/) and choose the appropriate version for your computer. Then follow the installation instruction. You should see a window like this: <img width="1025" alt="Screen Shot 2022-09-29 at 10 27 05 PM" src="https://user-images.githubusercontent.com/78475359/193196663-6f76332f-7dc6-4da5-9e79-046b349c211d.png">
  2. [Install OpenSSH](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui) if you are using Windows, or OpenSSH client for Non-Windows users.
*  Connect to server using ssh
      1. Open a terminal in VScode (Ctrl or Command + `)
      Type in 
      ```
      $ ssh cs15lfa22zz@ieng6.ucsd.edu
      ```
      But replace "zz" with your own course account.
      
      2. Type in Yes if you get a messsage asking you "Are you sure you want to continue connecting (yes/no/[fingerprint])?
      
      3. Then type in your password; note that you won't see anything as you type, so be careful when you type, or you can type your password somewhere else and copy and paste it into here.
      
          You will see this messsage if you successfully connect to the server:<img width="493" alt="Screen Shot 2022-09-29 at 10 40 51 PM" src="https://user-images.githubusercontent.com/78475359/193198282-2e7504f3-fb28-4d1f-8522-fe61043baad0.png">

          It's likely that you have to reset your password first and login afterward. You might wait 15-60min for the password to take into effect.
      
 * Trying some commands both with your computer and the remote computer
    * cd 
    * ls
    * pwd
    * mkdir
    * cp
    * cat /home/linux/ieng6/cs15lfa22/public/hello.txt
    * exit/ctrl-D (to log out remote server)
    You will see something like this:
    <img width="654" alt="Screen Shot 2022-09-29 at 10 50 41 PM" src="https://user-images.githubusercontent.com/78475359/193199396-38454500-5dff-4259-aaf0-4b0a250e8a7f.png">

    <img width="558" alt="Screen Shot 2022-09-29 at 10 50 06 PM" src="https://user-images.githubusercontent.com/78475359/193199350-e3508bcc-e86a-416b-ae22-f1b047c92f4a.png">

* Moving Files over SSH with scp
  1. Create a java file named **WhereAmI.java** with the following code
    ```
    class WhereAmI {
      public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
      }
    }
    ```
  2. Open a terminal and copy the file to remote server
      type 
      ```
      scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/

      ```
      where zz is replaced by your unique account name.
      Enter password. 
  3. If you successfully logged into remote server, type **ls** and see if the file is there. You should see something like this.<img width="229" alt="Screen Shot 2022-09-29 at 11 01 49 PM" src="https://user-images.githubusercontent.com/78475359/193200909-21a3b942-5932-43c6-be11-51bd53b960ff.png">Run code that you just copied both locally and on remote server with:
   
    ```
    javac WhereAmI.java
    java WhereAmI
    ```
    
   And you will see this result:
   
   <img width="331" alt="Screen Shot 2022-09-29 at 11 19 29 PM" src="https://user-images.githubusercontent.com/78475359/193203550-da4bd579-66d1-4374-bba8-cb18a8dc332d.png">
   <img width="363" alt="Screen Shot 2022-09-29 at 11 21 20 PM" src="https://user-images.githubusercontent.com/78475359/193203819-9f76522c-e4ff-4e4a-b822-21e28ce72913.png">
   
   The output will be different because the getProperty function gets the property of your computer in the first run and the property of the remote server in the second run.
   

   
* Using SSH keys for more convient access
  1. Set up using 
      ```
      ssh-keygen 
      ```
     And you will see message like this:
     <img width="577" alt="Screen Shot 2022-09-29 at 11 35 05 PM" src="https://user-images.githubusercontent.com/78475359/193205867-254710df-4616-4c36-a921-d7ec530c93f7.png">
     
   2. Make a directory on remote server named .ssh with 
      ```
      mkdir .ssh
      ```
   3. Now you can ssh and scp on your computer without entering password of your account:
     <img width="646" alt="Screen Shot 2022-09-29 at 11 37 08 PM" src="https://user-images.githubusercontent.com/78475359/193206207-1dce3240-b868-4946-a186-209d7696dc6a.png">

* Optimizing Remote Running

  * When you ssh, you can type the command at the end of the ssh command to execute the command then automatically logging out. 
    For example:
    <img width="388" alt="Screen Shot 2022-09-29 at 11 40 06 PM" src="https://user-images.githubusercontent.com/78475359/193206648-03b78359-324c-4191-9851-2b559bb91d0a.png">

    



  
      



