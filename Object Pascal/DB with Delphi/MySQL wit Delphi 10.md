https://blogs.embarcadero.com/learn-a-quick-way-to-connect-to-a-mysql-database-with-the-delphi-firedac-access-sample-app/


# Delhi 10 with MySQL
Use `FireDAC`

**Components used in the Sample App:**
-   `TFDQuery` : To execute SQL queries, browse the result sets, and edit the result set records.
-   `TFDPhysMySQLDriverLink`: To link the MySQL driver to an application and set it up. In general, it is enough to only include the `FireDAC.Phys.MySQL` [](http://firedac.phys.mysql/)unit into your application uses clause. The [TFDPhysMySQLDriverLink](http://docwiki.embarcadero.com/Libraries/Sydney/en/FireDAC.Phys.MySQL.TFDPhysMySQLDriverLink) component can be used to specify: The [VendorHome](http://docwiki.embarcadero.com/Libraries/Sydney/en/FireDAC.Phys.TFDPhysDriverLink.VendorHome) – the MySQL installation root folder. The [VendorLib](http://docwiki.embarcadero.com/Libraries/Sydney/en/FireDAC.Phys.TFDPhysDriverLink.VendorLib) – the name and the optional path to the MySQL client library.
-   `TFDConnection` : To establish a connection to a DBMS and to manage associated datasets.
-   And some of the UI components, like TDBGrid,TDBComboBox, TFDGUIxWaitCursor1, TFDGUIxLoginDialog1, TFDGUIxErrorDialog1

------
1. Get `libmysql.dll`
	1. 32 bits or 64bits
	2. To get libmysql.dll go to MySQL Connect bin or lib folder, look for it in the following paths.
		1.  For 32 bits: C:\Program Files (x86)\MySQL\… (Connector bin or lib folder)
		2.  For 64 bits: C:\Program Files\MySQL\… (Connector bin or lib folder)



