Fix-Warning-SplFileInfo-CakePHP
===============================

If your application show this message or similar:

** Warning: **[SplFileInfo::openFile]()(/var/www/html/MyProject/tmp/cache/persistent/._cake_core_file_map): failed to open stream: Permission denied in /var/www/MyProject/Vendor/cakephp/cakephp/lib/Cake/Cache/Engine/FileEngine.php on line xxx


Edit the file core.php (** Config/core.php **)

´´´
Cache::config ( '_cake_core_' , array ( 
    'engine'  => $engine , 
    'prefix'  =>  'cake_core_' , 
    'path'  => CACHE .  'persistent'  . DS , 
    'serialize'  =>  ( $engine ===  'File' ), 
    'duration'  => $duration , 
    'mask'  =>  0666 
));

Cache::config ( '_cake_model_' , array ( 
    'engine'  => $engine , 
    'prefix'  =>  'cake_model_' , 
    'path'  => CACHE .  'models'  . DS , 
    'serialize'  =>  ( $engine ===  'File' ), 
    'duration'  => $duration , 
    'mask'  =>  0666 
));

´´´


