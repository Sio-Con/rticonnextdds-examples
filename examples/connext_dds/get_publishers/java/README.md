# Example Code: get_publishers

## Building Java Example

Before compiling or running the example, make sure the environment variable
`NDDSHOME` is set to the directory where your version of *RTI Connext* is
installed.

Run *rtiddsgen* with the `-example` option and the target architecture of your
choice (e.g., *i86Win32VS2010* or *i86Linux2.6gcc4.4.5*). The *RTI Connext Core
Libraries and Utilities Getting Started Guide* describes this process in detail.
Follow the same procedure to generate the code and build the examples. **Do not
use the `-replace` option.** Assuming you want to generate an example for
*i86Win32VS2010* run:

```sh
rtiddsgen -language Java -example i86Linux2.6gcc4.4.3 Foo.idl
```

You will see messages that look like this:

```plaintext
File C:\local\get_publishers\java\FooPublisher.java already exists and
will not be replaced with updated content. If you would like to get a new file
with the new content, either remove this file or supply -replace option.
File C:\local\get_publishers\java\FooPublisher.java already exists and
will not be replaced with updated content. If you would like to get a new file
with the new content, either remove this file or supply -replace option.
```

This is normal and is only informing you that the subscriber/publisher code has
not been replaced, which is fine since all the source files for the example are
already provided.

Before compiling in Java, make sure that the desired version of the *javac*
compiler is in your `PATH` environment variable.

On *Windows* systems run:

```sh
javac -classpath .;%NDDSHOME%\lib\java\nddsjava.jar Foo.java FooSeq.java FooTypeSupport.java FooTypeCode.java FooDataReader.java FooDataWriter.java FooSubscriber.java FooPublisher.java
```

On *UNIX* systems run:

```sh
javac -classpath .:$NDDSHOME/lib/java/nddsjava.jar Foo.java FooSeq.java FooTypeSupport.java FooTypeCode.java FooDataReader.java FooDataWriter.java FooSubscriber.java FooPublisher.java
```

## Running Java Example

In two separate command prompt windows for the publisher and subscriber. Run the
following commands from the example directory (this is necessary to ensure the
application loads the QoS defined in *USER_QOS_PROFILES.xml*):

On *Windows* systems run:

```sh
java -cp .;%NDDSHOME%\lib\java\nddsjava.jar FooPublisher <domain_id>
```

On *UNIX* systems run:

```sh
java -cp .:$NDDSHOME/lib/java/nddsjava.jar FooPublisher <domain_id>
```

The applications accept one argument:

1.  The `<domain_id>`. Both applications must use the same domain ID in order to
    communicate. The default is 0.
