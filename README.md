# How-to-enable-ftp-in-AWS-EC2-instance-and-access-it-using-filezilla
In AWS EC2, you can connect and access files using sftp with your pem key file. In case if you want to access the ec2 instance using ftp not sftp, here we go.

irst create an instance in AWS.
Usually Ec2 instance are accessible via pem file. To override that we have to enable user with password login.
To enable password authentication in EC2 instance,
Run the following command

     sudo vi /etc/ssh/sshd_config
Edit value
        
    PasswordAuthentication:yes
Now set a password for the user ‘ubuntu’.
    
    sudo passwd ubuntu
Enter the password.
Restart sshd

    sudo service sshd restart
To access the ec2 instance through ftp, you need to install vsftpd

    sudo apt install vsftpd
We have to configure vsftpd to allow access
   
     listen=YES
     listen_ipv6=NO
     write_enable=YES
     allow_writeable_chroot=YES
Then restart vsftpd

     sudo service vsftpd restart
Create a folder for ftp access and give permission for that folder

     mkdir /home/ubuntu/ftpFolder
     sudo chown -R ubuntu /home/ubuntu/ftpFolder
If you are using Filezilla to access the files, you have to enable fallback mode to work properly.
In Filezilla, change transfer mode to Active, and enable allow fallback
Edit>>Settings>>Connection>>FTP

Try connecting the site using ftp in Filezilla using user host address, username and password.
Enjoy !!!!
