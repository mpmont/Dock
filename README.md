Dock
====

CodeIgniter 3 Namespace Loader

# Installation
Copy the Dock.php file to your application/libraries folder.

# Loading Dock
```
$this->load->library('dock');
```

# Using Dock
Dock expects that your namespaced library or model follows a folder and file structure according to its name.
Ex:
If your namespaced library was called: Foo\Bar\Test

Then Dock expects your CodeIgniter library folder to look similar to this:
application/libraries/Foo/Bar

and Dock expects you to have a file in the final folder called:
Test.php

To load a namespaced library 
```
$this->dock->library('Foo\Bar\Test');
```

You can now access the namespaced class via:
```
$this->Foo->Bar->Test;
```

You can even send construct parameters
```
$this->dock->library('Foo\Bar\Test',array('Param1','Param2'));
```

You can even rename your class object
```
$this->dock->library('Foo\Bar\Test',array('Param1','Param2'),'Swim');
//$this->Foo->Bar->Swim;
```