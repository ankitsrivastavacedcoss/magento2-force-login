# Force Login Module for Magento® 2
The **Force Login** Module for *Magento® 2* allows you to restrict which pages a visitor is
able to see. Visitors get redirected to the login page if the page is not marked visitable.
The **Force Login** Module for *Magento® 2* is especially useful for merchants serving only a specific
group of users, e.g. enterprise related business partners and need to ensure that only those users are
able to browse the the website or the product catalog.

## Features:
* Force your guest visitors to log in first (or register), before allowing them to visit your pages and catalog
* Administration: Manage the whitelist rules by the GUI in the administration area
* ACL: Restrict the administration of whitelist rules to certain backend user groups
* Whitelisting: Define url rules as pattern to define which pages guest visitors can visit without logging in first
* Multistore-Support: Define if whitelist rules either apply globally or for specific stores

## Installation
The preferred way of installing `bitexpert/magento2-force-customer-login` is through Composer. Simply add `bitexpert/magento2-force-customer-login` 
as a dependency:

```
composer.phar require bitexpert/magento2-force-customer-login
```

Optional you can download the latest version [here](https://github.com/bitExpert/magento2-force-login/releases) and install the
decompressed code in your projects directory under *app/code/bitExpert/ForceCustomerLogin*.  

## Post-Install

After the installment of the module source code, the module has to be enabled by the *Magento® 2* CLI.

```
bin/magento module:enable bitExpert_ForceCustomerLogin
```

## System Upgrade

After enabling the module, the *Magento® 2* system must be upgraded. 

If the system mode is set to *production*, run the *compile* command first. This is not necessary for the *developer* mode.
```
bin/magento setup:di:compile
```

To upgrade the system, the *upgrade* command must be run.
```
bin/magento setup:upgrade
```

## Clear Cache

At last, the *Magento® 2* should be cleared by running the *flush* command.
```
bin/magento cache:flush
```

Sometimes, other cache systems or services must be restarted first, e.g. Apache Webserver and PHP FPM.

# User Guide
Find the complete user guide [here](./docs/UserGuide.pdf "User Guide").

## How to use
The usage of the **Force Login** Module for *Magento® 2* is applied implicitly by redirecting visitors 
if the called URI does not match any configured whitelisted url rules.

### Whitelisting

Whitelisting is based upon the usage of rules. The rule syntax uses the [RegEx](https://en.wikipedia.org/wiki/Regular_expression) (regular expression) pattern.
By default, some static rules are already listed. The following example shows, how to add a whitelist entry for the homepage (startpage).

Navigate to the **Overview Grid** and use the *Add Entry* button.

- Enter **Homepage** into the text field beside from the **Label** label.
- Enter **^/?$** into the text field beside from the **Url Rule** label.
- Select **All Stores** from the selection field beside from the **Store** label.

Use the **Save** button in the upper menu. After being redirected to the **Overview Grid**, the new 
entry should appear to the list and the systems homepage should be available for guest visitors.

## How to configure

### Navigation
Navigating through the *Magento® 2* backend menu by clicking onto **Customers** you must see a new menu 
entry **Forced Login Whitelist**. 

Enter this menu entry.

![alt text](./resources/ui_step_01.png "UI Navigation")

### Overview Grid
You can add new entries by clicking on the *Add Entry* button in the upper right corner ( **1** ), [see below](#detail-form). 
The grid ( **2** ) contains all existing whitelisted *Url Rules*, for which the forced redirect to the *Customer Login Page* is omitted.
The *Url Rules* ( **3** ) are part of a regular expression checking on the called *Url* and tries to match against the whitelist.
*Url Rules* may be related to all stores or to a specific one ( **4** ). All rules except some mandatory ones are editable ( **5** ) and removeable ( **6** ).

![alt text](./resources/ui_step_02.png "UI Grid")

### Detail Form
You can return to the *Overview Grid* by using the *Back* button ( **1** ). The *Label* value has only declarative character and
is for information purpose only ( **2** ). The *Url Rule* is part of a regular expression checking on the called 
*Url* and tries to match against the whitelist ( **3** ). *Url Rules* may be related to all stores or to a specific one ( **4** ).
Persist the rule by using the *Save* button ( **5** ).

![alt text](./resources/ui_step_03.png "UI Form")

## Contribution
Feel free to contribute to this module by reporting issues or create some pull requests for improvements.

## License
The **Force Login** Module for *Magento® 2* is released under the Apache 2.0 license.
