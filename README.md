# Dock

CodeIgniter 3 Namespace Loader

# Table Of Contents
1. <a href="#1">Installation</a>
2. <a href="#2">Loading Dock</a>
3. <a href="#3">What is Dock</a>
4. <a href="#4">Loading Libraries</a>
5. <a href="#5">Loading Models</a>
6. <a href="#6">Loading Files</a>
7. <a href="#7">Loading Composer Packages</a>
8. <a href="#8">Additional Notes</a>
<hr />

### <a name="1">1-Installation</a>
Copy the Dock.php file to your application/libraries folder.
<hr />

### <a name="2">2-Loading Dock</a>
```
$this->load->library('dock');
```
<hr />

### <a name="3">3-What is Dock</a>
Dock is a class loader for [CodeIgniter](http://github.com/ellislab/codeigniter) that will load namespaced classes and make them available the same way CodeIgniter classes are accessed via $this->Something->something. Dock was created for people who like the traditional CodeIgniter way of accessing classes but aren't ready to use a full blown [Composer](http://www.google.com) setup yet. 

### <a name="4">4-Loading Libraries</a>
Dock expects that your namespaced library follows a folder and file structure according to its name.

Ex: If your namespaced library was called: Foo\Bar\Test

Then Dock expects your CodeIgniter library folder to look similar to this:
application/libraries/Foo/Bar

and Dock expects you to have a file in the final file called: Test.php

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

You may even rename your class object
```
$this->dock->library('Foo\Bar\Test',array('Param1','Param2'),'Swim');
//$this->Foo->Bar->Swim;
```
<hr />

### <a name="5">5-Loading Models</a>
Dock expects that your namespaced model follows a folder and file structure according to its name.

Ex:If your namespaced model was called: Baz\Bar\Test

Then Dock expects your CodeIgniter library folder to look similar to this:
application/models/Baz/Bar

and Dock expects you to have a file in the final file called: Test.php

To load a namespaced model
```
$this->dock->model('Baz\Bar\Test');
```

You can now access the namespaced model via:
```
$this->Baz->Bar->Test;
```

You can even send construct parameters
```
$this->dock->model('Baz\Bar\Test',array('Param1','Param2'));
```

You may even rename your class object
```
$this->dock->model('Baz\Bar\Test',array('Param1','Param2'),'Super');
//$this->Baz->Bar->Super;
```
<hr />

### <a name="6">6-Loading Files</a>
As with loading libraries and models Dock can also load files such as composer files as long as you provide a path. Again
the folder and file structure must match the namespace.

Ex.
```
$this->dock->file('path/without/filename','Name\Space\Name');
```
<hr />

### <a name="7">7-Composer Packages</a>
You can also use Dock to load Composer packages the traditional way within CodeIgniter. Make sure you have Composer enabled in your CodeIgniter project and then call something similar to this:

Ex.
```
$this->dock->composer('Some\Package\Name');
```

You can even send construct parameters
```
$this->dock->composer('Some\Package\Name',array('Param1','Param2'));
```

You may even rename your class object
```
$this->dock->composer('Some\Package\Name',array('Param1','Param2'),'SuperPackage');
//$this->Some->Package->SuperPackage;
<hr />

### <a name="8">8-Additional notes</a>
Dock uses reflection to pass your start up parameters to your namespaced class. If you choose not to use reflection for one reason or an
other you can disable this behavior by changing the class property use_reflection to false just keep in mind that you will only be able to pass 1 parameter to your construct.