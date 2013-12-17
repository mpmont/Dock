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

## Loading Libraries
Dock expects that your namespaced library follows a folder and file structure according to its name.
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

## Loading Models
Dock expects that your namespaced model follows a folder and file structure according to its name.
Ex:
If your namespaced model was called: Baz\Bar\Test

Then Dock expects your CodeIgniter library folder to look similar to this:
application/models/Bar/Bar

and Dock expects you to have a file in the final folder called:
Test.php

To load a namespaced library 
```
$this->dock->model('Baz\Bar\Test');
```

You can now access the namespaced class via:
```
$this->Baz->Bar->Test;
```

You can even send construct parameters
```
$this->dock->model('Baz\Bar\Test',array('Param1','Param2'));
```

You can even rename your class object
```
$this->dock->model('Baz\Bar\Test',array('Param1','Param2'),'Super');
//$this->Baz->Bar->Super;
```

## Loading Files
As with loading libraries and models Dock can also load files such as composer files as long as you provide a path. Again
the folder and file structure must match the namespace.

Ex. Loading Illuminate\Database
```
$this->dock->file(FCPATH.'vendor'.DIRECTORY_SEPARATOR.'Illuminate'.DIRECTORY_SEPARATOR.'Database','Illuminate\Database\Capsule\Manager');
```