# ZF Fundamentals June 2019

Class Repository: https://github.com/dbierer/zf-fund-jun-2019
## Labs
* Recommendations
  * Add `ini_set('display_errors',1);` in `/onlinemarket.work/config/development.config.php`
  * From `/home/vagrant/Zend/workspaces/DefaultWorkspace/onlinemarket.work` run `composer update` after installing the ZF skeleton app.  This will get rid of the notices you might see initially.
  * Error log file: `sudo tail /var/log/apache2/error.log`
* For Mon 17 Jun 2019
  * Lab: Using a Built-in Controller Plugin
  * Lab: Using a Custom Controller Plugin
  * Lab: New Controllers and Factories
    * For creating factories you can use, from the `onlinemarket.work` project root directory
    * This example creates the `PostControllerFactory`:
```
vendor/bin/create-factory-for-class Market\\Controller\\PostController
```
* For Fri 14 Jun 2019
  * Lab: Market Module
  * Lab: Index Controller
  * Lab: Initial View
* For Wed 12 Jun 2019
  * Lab: fix the Apache vhost definition for `onlinemarket.work` as shown below
  * Lab: install the Zend Framework skeleton app as described in the lab instructions
    * Recommendation: don't do steps 4 and 5 (so that you'll see the error message associated with missing modules later)
  * Lab: Integrating an Existing Module
    * https://github.com/zendframework/zend-developer-tools
## Class Discussion
* file:///D:/Repos/ZF-Level-1/Course_Materials/index.html#/4/31: s/be `setContent()` (no "S")
* file:///D:/Repos/ZF-Level-1/Course_Materials/index.html#/4/9: Zend\Mvc\Controller\Plugin\AbstractPlugin
* Why my new `Test` module was not responding: I needed to enable it in `/onlinemarket.work/config/modules.config.php`! (facepalm)
* New "home" for Zend Framework in the future:
  * https://www.linuxfoundation.org/blog/2019/04/lf-forms-laminas-project/
  * https://getlaminas.org/
* ZF2 vs. ZF3
  * https://github.com/dbierer/ZF2_ZF3_Side_by_SIde
## TODO
* RE: PRG controller plugin:
  * Find examples of usage
  * https://docs.zendframework.com/zend-mvc-plugin-prg/
* Need to modify the virtual host definition for `onlinemarket.work` as follows:
  * From the VM open a terminal window
  * Run `gedit` as the root user:
```
sudo gedit /etc/apache2/sites-available/onlinemarket.work.conf
```
  * Add `onlinemarket.work` after the `ServerName` directive
  * When done, the config file should look like this:
```
<VirtualHost *:80>
	ServerName onlinemarket.work
	DocumentRoot /home/vagrant/Zend/workspaces/DefaultWorkspace/onlinemarket.work/public
	<Directory /home/vagrant/Zend/workspaces/DefaultWorkspace/onlinemarket.work/public/>
		Options Indexes FollowSymlinks MultiViews
		AllowOverride All
		Require all granted
	</Directory>
</VirtualHost>
```
  * Perform a config test to make sure the syntax is correct:
```
sudo apachectl configtest
```
  * Restart the web server as follows:
```
sudo service apache2 start
```