# Install Microsoft Drivers for PHP for SQL Server
[Microsoft / msphpsql](https://github.com/Microsoft/msphpsql)

1. Install PHP, Apache2 and other required packages  
`sudo apt-get -y install php7.0 libapache2-mod-php7.0 mcrypt php7.0-mcrypt php-mbstring php-pear php7.0-dev apache2`

2. Install sqlcmd
```
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/mssql-tools.list
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install mssql-tools
sudo apt-get install unixodbc-dev
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
```
3. Test the installation. (optional but recomended)  
`sqlcmd -S <ip/hostname> -U <username> -P <password> -Q "SELECT @@VERSION"`

4. Install the driver  
```
sudo pecl install sqlsrv pdo_sqlsrv
sudo echo "extension= pdo_sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
sudo echo "extension= sqlsrv.so" >> /etc/php/7.0/apache2/php.ini
```

5. Restart Apache.  
`sudo service apache2 restart`

6. And you're done! Read more:  
Github: [Microsoft / msphpsql](https://github.com/Microsoft/msphpsql)  
Microsoft.com: [Create PHP apps using SQL Server on Ubuntu](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu/)
