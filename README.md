This is a stripped down version of a basic LidGDX project that displays an
unfortunate interaction I've been dealing with in another real use case.

The .java file in the core project has been slimmed down to _only_ import
Guava's BaseEncoding and declare a single BaseEncoding field.

The .java file in the html project has been slimmed down to do nothing but
import the core class.

The base gwt.xml file in the html project can be edited by adding or removing
    <inherits name="com.google.common.collect.Collect"/>
    
When this line is present, running `gradle war` from the base project will
show a compilation error in the GWT compilation:

Compiling module com.mygdx.game.GdxDefinition
   Validating units:
      [ERROR] Errors in 'com/google/common/io/super/com/google/common/io/BaseEncoding.java'
         [ERROR] Line 142: The constructor IOException(Throwable) is undefined
   [ERROR] Aborting compile due to errors in some input files

When this line is not present, running `gradle war` will complete successfully.

Any thoughts on why this is occuring?
