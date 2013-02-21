[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=n0ha&url=https://github.com/n0ha/yui-compressor-ant-task&title=yui-compressor-ant-task&language=en_GB&tags=github&category=software)

YUI Compressor Ant Task
-----------------------

Yahoo UI's great Rhino based compressor packaged as an Ant task.

Short introduction with examples: http://javaflight.blogspot.com/2008/01/introducing-yui-compressor-ant-task.html

### Quick way to set up

In your ant lib folder include:

* yui-compressor-ant-task-0.6.0.jar
* yui-compressor-2.4.8pre.jar (or whichever version of the YUI Compressor you prefer)
* guava-13.0.1.jar

and in `build.xml`

        <target name="minify">
          <taskdef name="yui-compressor" classname="net.noha.tools.ant.yuicompressor.tasks.YuiCompressorTask">
            <classpath>
              <pathelement location="${lib.ant}/yui-compressor-ant-task-0.6.0.jar"/>
              <pathelement location="${lib.ant}/guava-13.0.1.jar"/>
              <pathelement location="${lib.ant}/yuicompressor-2.4.8pre.jar"/>
            </classpath>
          </taskdef>
          <yui-compressor warn="false" munge="true" fromdir="${src.dir}" todir="${build.dir}">
            <include name="**/*.js"/>
          </yui-compressor>
        </target>

Note that this skips the HTML compressor included (but this should be as easy as adding in yet another jar file).

Changes
-------

* if `toDir` does not exist, the ant task will attempt to call `toDir.mkdirs()` and fail if this returns `false` (for some reason)
