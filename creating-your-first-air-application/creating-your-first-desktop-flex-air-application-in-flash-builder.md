<h1>Creating your first desktop Flex AIR application in Flash Builder</h1>

<div>
	<p>For a quick, hands-on illustration
		of how Adobe® AIR® works, use these instructions to create and package
		a simple SWF file-based AIR “Hello World” application using Adobe®
		Flash® Builder. </p>
	<p>If you haven’t already done so, download and install Flash Builder.
		Also, download and install the most recent version of Adobe AIR,
		which is located here: <a href="http://www.adobe.com/go/air">www.adobe.com/go/air</a>.</p>
	<ul></ul>
</div>
<div>
	<h2>Create an AIR project</h2>
	<div>
		<p>Flash
			Builder includes tools to develop and package AIR applications.</p>
		<p>You begin to create AIR applications in Flash Builder or Flex
			Builder in the same way that you create other Flex-based application
			projects: by defining a new project. </p>
		<ol>
			<li>
				<p>Open Flash Builder.</p>
			</li>
			<li>
				<p>Select File &gt; New &gt; Flex Project. </p>
			</li>
			<li>
				<p>Enter the project name as AIRHelloWorld. </p>
			</li>
			<li>
				<p>In Flex, AIR applications are considered an application type.
					You have two type options:</p>
				<ul>
					<li>
						<p>a web application that
							runs in Adobe® Flash® Player</p>
					</li>
					<li>
						<p>a desktop application that runs in Adobe AIR</p>
					</li>
				</ul>
				<p>Select
					Desktop as the application type. </p>
			</li>
			<li>
				<p>Click Finish to create the project.</p>
			</li>
		</ol>
		<p>AIR projects initially consist of two files: the main MXML file
			and an application XML file (known as the application descriptor
			file). The latter file specifies application properties. </p>
		<p>For more information, see <a
				href="http://help.adobe.com/en_US/Flex/4.0/UsingFlashBuilder/WS6b84a753ecd210fd-7fb8a08d12114b6a4cf-8000.html">Developing
				AIR applications with Flash Builder</a>.</p>
	</div>
</div>
<div>
	<h2>Write the AIR application code</h2>
	<div>
		<p>To write the “Hello World” application code, you edit the
			application MXML file (AIRHelloWorld.mxml), which is open in the
			editor. (If the file isn't open, use the Project Navigator to open
			the file.) </p>
		<p>Flex AIR applications on the desktop are contained within the
			MXML WindowedApplication tag. The MXML WindowedApplication tag creates
			a simple window that includes basic window controls such as a title
			bar and close button. </p>
		<ol>
			<li>
				<p>Add a <samp>title</samp> attribute to the WindowedApplication
					component, and assign it the value <samp>"Hello World"</samp>:</p>
				<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt; 
&lt;s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009" 
                       xmlns:s="library://ns.adobe.com/flex/spark" 
                       xmlns:mx="library://ns.adobe.com/flex/mx" 
                       title="Hello World"&gt; 
&lt;/s:WindowedApplication&gt;</pre>
			</li>
			<li>
				<p>Add a Label component to the application (place it inside
					the WindowedApplication tag). Set the <samp>text</samp> property
					of the Label component to <samp>"Hello AIR"</samp>, and set
					the layout constraints to keep it centered, as shown here:</p>
				<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt; 
&lt;s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009" 
                       xmlns:s="library://ns.adobe.com/flex/spark" 
                       xmlns:mx="library://ns.adobe.com/flex/mx" 
                       title="Hello World"&gt; 
 
    &lt;s:Label text="Hello AIR" horizontalCenter="0" verticalCenter="0"/&gt; 
&lt;/s:WindowedApplication&gt;</pre>
			</li>
			<li>
				<p>Add the following style block immediately after the opening
					WindowedApplication tag and before the label component tag you just
					entered:</p>
				<pre>&lt;fx:Style&gt; 
    @namespace s "library://ns.adobe.com/flex/spark"; 
    s|WindowedApplication 
    { 
     
skinClass:ClassReference("spark.skins.spark.SparkChromeWindowedApplicationSkin"); 
        background-color:#999999; 
        background-alpha:"0.7"; 
    }          
&lt;/fx:Style&gt;</pre>
			</li>
		</ol>
		<p>These style settings apply to the entire application and render
			the window background a slightly transparent gray. </p>
		<p>The application code now looks like the following:</p>
		<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt; 
&lt;s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009" 
                       xmlns:s="library://ns.adobe.com/flex/spark" 
                       xmlns:mx="library://ns.adobe.com/flex/mx" 
                       title="Hello World"&gt; 
     
    &lt;fx:Style&gt; 
        @namespace s "library://ns.adobe.com/flex/spark"; 
        s|WindowedApplication 
        { 
         
skinClass:ClassReference("spark.skins.spark.SparkChromeWindowedApplicationSkin"); 
            background-color:#999999; 
            background-alpha:"0.7"; 
        }          
    &lt;/fx:Style&gt; 
 
    &lt;s:Label text="Hello AIR" horizontalCenter="0" verticalCenter="0"/&gt; 
&lt;/s:WindowedApplication&gt;</pre>
		<p>Next, you will change some settings in the application descriptor
			to allow the application to be transparent:</p>
		<div>
			<ol>
				<li>
					<p>In the Flex Navigator pane, locate the application
						descriptor file in the source directory of the project. If you named
						your project AIRHelloWorld, this file is named AIRHelloWorld-app.xml.</p>
				</li>
				<li>
					<p>Double-click the application descriptor file to edit it in
						Flash Builder.</p>
				</li>
				<li>
					<p>In the XML code, locate the commented lines for the <samp>systemChrome</samp> and
						<samp>transparent</samp> properties
						(of the <samp>initialWindow</samp> property). Remove the comments.
						(Remove the <samp>"&lt;!--"</samp> and <samp>"--&gt;"</samp> comment
						delimiters.)</p>
				</li>
				<li>
					<p>Set the text value of the <samp>systemChrome</samp> property
						to <samp>none</samp>, as in the following:</p>
					<pre>&lt;systemChrome&gt;none&lt;/systemChrome&gt;</pre>
				</li>
				<li>
					<p>Set the text value of the <samp>transparent</samp> property
						to <samp>true</samp>, as in the following:</p>
					<pre>&lt;transparent&gt;true&lt;/transparent&gt;</pre>
				</li>
				<li>
					<p>Save the file.</p>
				</li>
			</ol>
		</div>
	</div>
</div>
<div>
	<h2>Test the AIR application</h2>
	<div>
		<p>To test the application code that you’ve written, run it
			in debug mode. </p>
		<ol>
			<li>
				<p>Click the Debug button <img src="../img/FlexBuilderDebugIcon1.png"> in
					the main toolbar. </p>
				<p>You can also select the Run &gt; Debug
					&gt; AIRHelloWorld command.</p>
				<p>The resulting AIR application
					should look like the following example: </p>
				<div xmlns:fn="http://www.w3.org/2005/xpath-functions" xmlns:fo="http://www.w3.org/1999/XSL/Format"
					xmlns:xs="http://www.w3.org/2001/XMLSchema"><img alt="" src="../img/HelloWorldApolloScreenshot.png">
				</div>
			</li>
			<li>
				<p>Using the <samp>horizontalCenter</samp> and <samp>verticalCenter</samp> properties
					of the Label control, the text is placed in the center of the window.
					Move or resize the window as you would any other desktop application. </p>
			</li>
		</ol>
		<div><span>Note: </span>If the application does not compile, fix any
			syntax or spelling errors that you inadvertently entered into the
			code. Errors and warnings are displayed in the Problems view in
			Flash Builder. </div>
	</div>
</div>
<div>
	<h2>Package, sign, and run your AIR application</h2>
	<div>
		<p>You are now ready to package the "Hello World" application
			into an AIR file for distribution. An AIR file is an archive file
			that contains the application files, which are all of the files
			contained in the project’s bin folder. In this simple example, those
			files are the SWF and application XML files. You distribute the
			AIR package to users who then use it to install the application.
			A required step in this process is to digitally sign it. </p>
		<ol>
			<li>
				<p>Ensure that the application has no compilation errors
					and runs as expected. </p>
			</li>
			<li>
				<p>Select Project &gt; Export Release Build. </p>
			</li>
			<li>
				<p>Check that the AIRHelloWorld project and AIRHelloWorld.mxml
					application are listed for project and application. </p>
			</li>
			<li>
				<p>Select Export as signed AIR package option. Then click Next.</p>
			</li>
			<li>
				<p>If you have an existing digital certificate, click Browse
					to locate and select it. </p>
			</li>
			<li>
				<p>If you must create a new self-signed digital certificate,
					select Create. </p>
			</li>
			<li>
				<p>Enter the required information and click OK. </p>
			</li>
			<li>
				<p>Click Finish to generate the AIR package, which is named
					AIRHelloWorld.air.</p>
			</li>
		</ol>
		<p>You can now install and run the application from the Project
			Navigator in Flash Builder or from the file system by double-clicking
			the AIR file.</p>
	</div>
</div>

<!-- BEGIN USER PREFERENCES -->

<!-- END USER PREFERENCES -->

<div>

    <div>&nbsp;</div>

</div>
