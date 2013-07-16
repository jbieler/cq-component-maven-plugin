The Component Plugin requires 2 maven configurations to work propertly.  The first is the plugin configuration itself and the
second is the addition of a maven dependency that contains the required annotations and abstract classes/interfaces used to extends the plugin.

Maven Plugin
-----------

```xml
<plugin>
    <groupId>com.citytechinc.cq.cq-component-plugin</groupId>
    <artifactId>cq-component-maven-plugin</artifactId>
    <version>1.1.1</version>
    <extensions>true</extensions>
    <executions>
        <execution>
            <goals>
                <goal>component</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <componentPathBase>jcr_root/apps/client/components</componentPathBase>
        <componentPathSuffix>content</componentPathSuffix>
        <defaultComponentGroup>Client Group</defaultComponentGroup>
        <transformerName>camel-case</transformerName>
    </configuration>
</plugin>
```

<table class="table table-striped break-words-table">
	<thead>
		<tr>
			<th>Element</th>
			<th>Type</th>
			<th>Default</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>componentPathBase</td>
			<td>String</td>
			<td></td>
			<td>
				The content path to your project's components within the apps content tree.  The full path to which
	          files for an individual component will be written is:
	          componentPathBase + / + componentPathSuffix + / + component name (annotated per component or based
	          on the name of the component class if not annotated).  The component path as a whole can be overridden
	          at the component level via the path property of the @Component annotation.
			</td>
		</tr>
		<tr>
			<td>componentPathSuffix</td>
			<td>String</td>
			<td>content</td>
			<td>See the description of componentPathBase for an explanation of how this property is used in
	          the construction of a path to which component files will be written.
			</td>
		</tr>
		<tr>
			<td>defaultComponentGroup</td>
			<td>String</td>
			<td></td>
			<td>The group to which Components whose files are generated via this plugin will be added in the
	          CQ Sidekick.  This can be overridden at the component level via the group property of the
	          @Component annotation.
			</td>
		</tr>
		<tr>
			<td>transformerName</td>
			<td>String</td>
			<td></td>
			<td>The name of the transformer used to change from a the name of a class to the folder in the jcr.  The 
				defaults available are:
				<ul>
					<li>camel-case: Makes the class name camel case</li>
					<li>lower-case: Lowercases the class name</li>
					<li>lower-case-dash: Lower cases the class and sperates words with dashes</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>


Maven Dependency
-----------


```xml
<dependency>
	<groupId>com.citytechinc.cq.cq-component-plugin</groupId>
	<artifactId>cq-component-annotations</artifactId>
	<version>1.1.1</version>
</dependency>
```

This will allow you to use the Annotations necessary to create the xml files.