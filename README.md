# magento-notes
Useful code and links for Magento that i found or wrote.


:warning: Add a file to root and use these codes

# Get list of installed modules config path list Magento 1.9

```
require_once 'app/Mage.php';
umask(0);
Mage::app('admin');

$fileName = 'config.xml';
$modules = Mage::getConfig()->getNode('modules')->children();
foreach ($modules as $modName => $module) {
    if ($module->is('active')) {
        $configFile = Mage::getConfig()->getModuleDir('etc', $modName) . DS . $fileName;
        
        if (file_exists($configFile)) {
            echo $configFile;
            echo "<hr/>";
        }
    }
}

```

