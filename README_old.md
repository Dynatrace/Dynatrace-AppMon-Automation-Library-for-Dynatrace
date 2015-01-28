# Automation Library for dynaTrace

## Overview

| Name | Automation Library for dynaTrace to integrate dynaTrace in an automated environment such as a build or automated test environment
| :--- | :---
| Description | Automation is key in different phases of the Software Development Lifecycle. Builds are automated by using build-servers that also execute all unit and integration tests to ensure the basic quality criteria for a build before it gets deployed to the next stage. Functional as well as load-tests can be automated to test applications that come out of the build-environment to ensure full functionality, performance and scalability.dynaTrace provides this Automation Library to easily integrate dynaTrace in your **Continuous Integration** or Test Automation Environment such as **Ant**, **Maven**, **Hudson**, ....The automation library provides contextual information such as the version/revision/build number to be used by the dynaTrace Automation Test Center and visible in the Test Automation Dashlet. The library also includes reporting capabilities.
|Version|1.0
|dynaTrace Versions| >= 5.5
|Author|dynaTrace software
|License|[dynaTrace BSD](dynaTraceBSD.txt)
|Support|[Supported](https://community.compuwareapm.com/community.compuwareapm.com/community/display/DL/Support+Levels#SupportLevels-Supported)
|Sample Downloads| [dynaTrace Automation Walkthrough including Samples for JUnit and Selenium](https://community.compuwareapm.com/community.dynatrace.com/community/display/DOCDT50/Automated+Performance+Analysis+in+Continuous+Integration)
||[dynaTrace Automation Samples for Ant and Maven](dynaTraceAutomationSample.zip)

###Download for Java

**dynaTrace 6.0:**

  * [Automation Library ONLY](com.dynatrace.diagnostics.automation_6.0.0.6733.zip)

  * [Ant Integration ONLY](com.dynatrace.integration.ant_6.0.0.6733.zip)

  * [Maven Plugin](dtAutomation.jar)  
  
**dynaTrace 5.6:**

  * [Automation Library ONLY](com.dynatrace.diagnostics.automation_5.6.0.5713.zip)

  * [Ant Integration ONLY](com.dynatrace.integration.ant_5.6.0.5713.zip)

  * [Maven Plugin](dtAutomation.jar)  
  
  
**dynaTrace 5.5:**

  * [Automation Library ONLY](com.dynatrace.diagnostics.automation.jar)

  * [Ant Integration ONLY](com.dynatrace.integration.ant.jar)  
  
###Download for .NET

**dynaTrace 4.x, 5.x**

  * [NANT Task Library](https://community/display/DL/NANT+Task+Library)

  * [MSBuild Tasks Library](https://community/display/DL/MSBuild+Tasks+Library)

  * [.NET Command Library](https://community/display/DL/.NET+Command+Library) (Only necessary if running prior to dynaTrace v3.5. dynatrace 3.5+ already includes this library) 



## Description

The automation library enables FULL Automation of dynaTrace by leveraging the REST interfaces of the dynaTrace Server. The automation library includes Ant Tasks, Maven Goals and a console application
to execute the following actions on the dynaTrace Server:

  * **Start/Stop Session Recording**: Returns the actual recorded session name 

  * **Set Test Information**: Sets information about the tested built to be used by Test Automation Center 

  * **Clear Session**: Clears the live session 

  * **Reanalyze Stored Sessions**: triggers business transaction analysis of a stored session 

  * **Enable/Disable Profile**

  * **Activate Configuration**: Activates a configuration within a system profile 

  * **Get Agent Information**: Either returns the number of connected agents or specific information about a single agent 

  * **Create Memory/Thread Dumps**: Triggers memory or thread dumps for a specific connected agent 

  * **Restart Server/Collector**

The library also includes reporting capabilities that were previously implemented in separate Ant-Libraries:

  * Reporting on Dashboards: creates HTML reports based on dashboards 

  * Architecture Validation: allows to perform architecture validation rules on captures PurePaths 

The Download package includes:

dtAutomation{VERSION}.zip

Automation Library for dynaTrace {VERSION} including implemenation for Ant, Maven2 and Console Application. Also includes a JUnit Runner for Selenium and a separate dtTaskDefs.xml that defines and
documents all available Ant-Tasks

dynaTraceForMaven.zip

Automation Library packaged to be used with the Maven2 Plugin Repository (includes description files and correct file structure)

com.dynatrace.diagnostics.automation.jar

Automation Library for 3.2.x including implemenation for Ant, Maven2 and Console Application

dynaTraceForMaven.zip

Automation Library for 3.2.x packaged to be used with the Maven2 Plugin Repository (includes description files and correct file structure)

dynaTraceAutomationSample.zip

The package includes a sample build.xml for Ant, pom.xml for Maven2 and Dashboards and configuration files to be used for the Reporting and Architecture Validation feature

## Installation

### To be used with Ant

**For 3.5, 4 & 5**

  * Extract Automation Library Package to your local file system 

  * Under `lib/dynatrace` you find `dtTaskDefs.xml` (defines all Ant Task) and `com.dynatrace.diagnostics.automation.jar` (the actual automation library) 

  * Have a look at `build.xml` in the root directory as a sample on how to call the ant tasks 

**For 3.2.x**

  * Extract `com.dynatrace.diagnostics.automation.jar` to your local file system 

  * Define the ant tasks as shown in the `tTaskDefs.xml` file from the [sample package](attachments_24412211_7_dynaTraceAutomationSample.zip) or simple <import> this file with your existing Ant. 

  * Call the dynaTraceAnt Tasks in your Ant Targets - for an example see `build.xml` file in sample package 

### To be used with Maven

  * Extract `dynaTraceForMaven.zip` to your local file system. 

  * To install the dynaTrace Maven plugin, execute the following command: 
    
        mvn install:install-file -DgroupId=dynaTrace -DartifactId=dtAutomation -Dversion=3.5 -Dpackaging=maven-plugin -Dfile=<your download location>\dtAutomation\3.5\dtAutomation.jar

  * Define properties for the dynaTracegoals as shown in pom.xml from the sample package 

  * Invoke your maven goals, e.g.: mvn dynaTrace:dtAutomation:3.5:startRecording 

The dynaTracemaven plugin has the following identification (pluginGroupId:pluginArtifactId:pluginVerion): dynaTrace:dtAutomation:1.1

### To be used from the command line

  * Extract `com.dynatrace.diagnostics.automation.jar` to your local file system 

  * run the application without parameters to get usage information: 
    
        java -cp com.dynatrace.diagnostics.automation.jar com.dynatrace.diagnostics.automation.Console

  * username, password and serverUrl default back to localhost and admin/admin. These values can be passed in via command line or even via a `console.properties` file defining these 3 values 

### Usage

#### With Ant

A full example that includes calling JUnit and Selenium tests can be seen in the [Demo Application Package](https://community/display/DL/Demo+Applications). You can also download the `build.xml` as
shown later in this paragraph which is as part of [dtAutomation35.zip](attachments_39518414_4_dtAutomation35.zip) or the [3.2.x sample package](attachments_24412211_7_dynaTraceAutomationSample.zip).  
Use and import `dtTaskDefs.xml` in your existing Ant file. This file defines all TaskDefs and global properties that allow you to specify username, password, serverURL, ... Here is the full
`build.xml` file that is part of the download sample package. It includes a sample call to all TaskDefs including documentation of the properties:

    
    
    <project name="Sample dynaTrace Automation Ant file">
    	<description>
    		Shows how to use the dynaTrace Automation Ant Tasks
    	</description>
    	<!-- Import the dynaTrace Automation Tasks -->
    	<import file="lib/dynaTrace/dtTaskDefs.xml"/>
    	<!-- Setting defaults for Test Automation -->
    	<property name="dtVersionMajor" value="1" />
    	<property name="dtVersionMinor" value="0" />
    	<property name="dtVersionRevision" value="0" />
    	<property name="dtVersionMilestone" value="Milestone 1" />
    	<property name="dtVersionBuild" value="123" />
    	<property name="dtAgentGroup" value="GoSpaceFrontend" />
    	<!-- Enables GoSpace and actives GoSpace Light configuration
    		configuration and profilenames need are case sensitive
    	-->
    	<target name="EnableProfileAndActivateConfiguration">
    		<DtEnableProfile profileName="GoSpace" enable="true" />
    		<DtActivateConfiguration profileName="GoSpace" configuration="GoSpace light" />
    	</target>
    	<!-- Clears the live session of GoSpace -->
    	<target name="ClearSession">
    		<DtClearSession profileName="GoSpace" />
    	</target>
    	<!-- Sets Test Meta Data Information for Test Automation -->
    	<target name="SetTestInformationForTestAutomation">
    		<DtSetTestInformation versionMajor="${dtVersionMajor}" versionMinor="${dtVersionMinor}" versionRevision="${dtVersionRevision}"
    		  versionMilestone="${dtVersionMilestone}" versionBuild="${dtVersionBuild}" agentGroup="${dtAgentGroup}" setInformationStatusProperty="dtStatusProperty"/>
    		<echo message="Set Test Information with status : ${dtStatusProperty}" />
    	</target>
    	<!-- Retrieves the number of Connected Agents
    		Then queries the agent information for the first connected agent and the first GoSpaceFrontend agent
    		The requested information is stored in Ant Properties that can later be used by other tasks, e.g.: DtMemoryDump to identify the agent
    	 -->
    	<target name="GetAgentInfo">
    		<DtGetAgentInfo agentCountProperty="AgentCount" />
    		<echo message="Connected Agents: ${AgentCount}"></echo>
    		<DtGetAgentInfo agentNameProperty="AgentName" agentHostNameProperty="AgentHost" agentProcessIdProperty="AgentProcessId" infoForAgentByIndex="0" />
    		<echo message="First Agent: ${AgentName} - ${AgentHost} - ${AgentProcessId}"></echo>
    		<DtGetAgentInfo agentNameProperty="AgentName" agentHostNameProperty="AgentHost" agentProcessIdProperty="AgentProcessId" infoForAgentByName="GoSpaceFrontend" />
    		<echo message="First GoSpaceFrontend: ${AgentName} - ${AgentHost} - ${AgentProcessId}"></echo>
    	</target>
    	<!-- Takes a Memory and Thread Dump from a specific agent
    		We call GetAgentInfo first that retrieves the Agent Information for which the dump gets created
    	-->
    	<target name="TakeMemoryAndThreadDumps" depends="GetAgentInfo" >
    		<DtMemoryDump memoryDumpNameProperty="MemoryDumpName" profileName="GoSpace" agentName="${AgentName}" hostName="${AgentHost}" processId="${AgentProcessId}" />
    		<echo message="Created Memory Dump: ${MemoryDumpName}" />
    		<DtThreadDump threadDumpNameProperty="ThreadDumpName" agentName="${AgentName}" hostName="${AgentHost}" processId="${AgentProcessId}" />
    		<echo message="Created Thread Dump: ${ThreadDumpName}" />
    	</target>
    	<!-- Start Recording a new dynaTrace Session
    		The actual session name will be stored in the Ant Property "SessionName" which can later be used as input for other tasks, e.g.: ReanalyzeSession
    	-->
    	<target name="StartRecording">
    		<DtStartRecording profileName="GoSpace" sessionNameProperty="SessionName" sessionName="AntSession" sessionDescription="This Session is triggered by an Ant Task"  />
            <echo message="Start Recording SessionName: ${SessionName}" />
    	</target>
    	<!-- Stops current recording
    		The actual session name will be stored in the Ant Property "SessionName" which can later be used as input for other tasks, e.g.: ReanalyzeSession
    	-->
    	<target name="StopRecording">
    		<!-- The sleep is in there so that you can manually create some purepaths in the meantime that end up in the session -->
    		<sleep seconds="10"/>
    		<DtStopRecording profileName="GoSpace" sessionNameProperty="SessionName" />
    		<echo message="Stopped Recording SessionName: ${SessionName}" />
        </target>
    	<!-- Stops current recording and also reanalizes the session
    		In this case the System Profile name comes from the global dtProfile Property
    	-->
    	<target name="StopRecordingWithReanalyze">
    		<!-- The sleep is in there so that you can manually create some purepaths in the meantime that end up in the session -->
    		<sleep seconds="10"/>
    		<DtStopRecording doReanalyzeSession="true" reanalyzeStatusProperty="ReanalyzeStatus" />
    		<echo message="Stopped Recording SessionName and reanalized: ${SessionName} - ${ReanalyzeStatus}" />
        </target>
    	<!-- Reanalyzes a specific dynaTrace Session
    		We use the value stored in the SessionName property which falls set by StopRecording
    	-->
    	<target name="ReanalyzeSession">
    		<DtReanalyzeSession sessionName="${SessionName}" reanalyzeStatusProperty="ReanalyzeStatus" reanalyzeSessionTimeout="60000" reanalyzeSessionPollingInterval="5000" />
    		<echo message="Reanalyze finished? ${ReanalyzeStatus}" />
    	</target>
    	<!-- Combines the calls to Start/Stop and Reanalyze -->
    	<target name="StartStopRecordingAndReanalyze" depends="StartRecording,StopRecording,ReanalyzeSession" >
    	</target>
    	<!-- Combines the calls to Start and StopWithReanalyze -->
    	<target name="StartStopInclReanalyze" depends="StartRecording,StopRecordingWithReanalyze" >
    	</target>
    	<target name="DashboardReporting">
    		<!-- Queries a single dashboard and puts the result out to an XML File using XSLT to transform it to HTML -->
    		<DtReport dashboardname="Test" source="live:GoSpace" createHtml="true" xmlToFile="./results/report.xml"/>
    		<!-- Creates a dashboard report for every transaction or webrequest that is on the iterator dashborad
    			outputs all files in the report directory
    			an overview page is created to navigate through all result files
    		 -->
    		<DtReport dashboardname="RulesDashboard" iteratorDashboard="TransactionDashboard" source="live:GoSpace" createHtml="true" reportDir="./results"/>
    		<!-- Make sure that - when using Business Transactions on the Iterator or Data Dashboard to reanalyze stored sessions before running the report
    		    Either us DtReanalyzeSession or specify the reanalyzeSession="true" property for DtReport
    		-->
    	</target>
    	<target name="ArchitecturValidation">
    		<DtArchiVal source="live:GoSpace" archiValFile="archivalrules.xml" reportFile="./results/archivalreport.xml" errorProperty="ArchiValFailed"/>
    	</target>
    </project>

#### With Maven

The dynaTrace version in the maven package may still say 3.5 even though you downloaded the package for dynaTrace 4.x.

Download the Step-by-Step Guide on How to use Maven and WebDriver with dynaTrace: [MavenWebDriverIntegration.docx](attachments_93192226_1_MavenWebDriverIntegration.docx)

A full example can be seen in the pom.xml as part of the [sample package](attachments_24412211_7_dynaTraceAutomationSample.zip).  
Also look at description of the previous [Maven Plugin Page](Automation_Library_for_dynaTrace.html) that explains how to use the reporting and other maven goals that this plugin provides.

    
    
    <properties>
      <!-- Setting default values for dynaTrace Maven goals that operate on a system profile -->
      <dynaTrace.username>admin</dynaTrace.username>
      <dynaTrace.password>admin</dynaTrace.password>
      <dynaTrace.serverUrl>http://localhost:8020</dynaTrace.serverUrl>
      <dynaTrace.systemProfile>GoSpace</dynaTrace.systemProfile>
      <!-- This property will be used to store the actual Session Name for e.g.: Start/Stop Recording -->
      <dynaTrace.sessionNameProperty>dynaTrace.sessionName</dynaTrace.sessionNameProperty>
      <!-- Following is a list of properties for goal: startRecording -->
      <dynaTrace.sessionName>My Stored Session</dynaTrace.sessionName>
      <dynaTrace.sessionDescription>My stored Session Description</dynaTrace.sessionDescription>
      <dynaTrace.recordingOption>all</dynaTrace.recordingOption> <!-- other options: violations|timeseries -->
      <dynaTrace.sessionLocked>false</dynaTrace.sessionLocked>
      <dynaTrace.appendTimestamp>false</dynaTrace.appendTimestamp>
    </properties>

Now we can call the startRecording goal in the following way:

    
    
    mvn dynaTrace:dtAutomation:3.5:startRecording

You can inject the dynaTrace agent as part of surefire unit testing in Maven pom.xml with settings similar to this:

    
    
    <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.5</version>
    <configuration>
    <argLine>-agentpath:"C:\Program Files\dynaTrace\dynaTrace 5.0.0\agent\lib\dtagent.dll"=name=Maven,server=localhost:9998</argLine>
    </configuration>
    </plugin>

#### With Console Application

Launch the application without parameter to see all available options including some sample.

    
    
    java -cp com.dynatrace.diagnostics.automation.jar com.dynatrace.diagnostics.automation.Console

Following are some examples of which parameters to pass to start/stop recording, reanalyze session, ...

    
    
    -startrecording GoSpace "My Session" "My Description"
    -startrecording GoSpace "My Session" "My Description" violations true
    -stoprecording GoSpace
    -reanalyzesession "My Session"
    -enableprofile GoSpace false
    -activateconfiguration GoSpace "GoSpace light"
    -memorydump GoSpace GoSpaceFrontend MYMACHINE 2332 simple
    -threaddump GoSpace GoSpaceFrontend MYMACHINE 2332

### For Java Developers

The Automation Library includes the dynaTrace REST Automation SDK (com.dynatrace.diagnostics.automation.rest.sdk) which provides the helper class RESTEndpoint which exposes all important REST
Interfaces of the dynaTrace Server.  
Here is an example on how to use this helper class:

    
    
    // Start and Stop Session Recording
    RESTEndpoint endPoint = new RESTEndpoint("admin", "admin", "localhost");
    String sessionName = endPoint.startRecording("easyTravel", "Session1", "My Load Test Session", "all", true, false);
    System.out.println("Started recording Session: "+ sessionName);
    endPoint.stopRecording("easyTravel");
    // list all connected agents
    for(Agent agent : endPoint.getAgents()) {
      System.out.println("Agent Name: " + agent.getName());
    }

[Download the JavaDoc](attachments_102629479_1_javadoc_RESTEndpoint.zip) for the RESTEndpoint.

### dynaTraceReporting

For a detailed description about the usage and samples see the documentation on [Ant Task for dynaTrace 3.1 Reporting](https://community/display/DL/Ant+Task+for+dynaTrace+3.1+Reporting)

### Architecture Validation

This feature allows you to define architectural rules like "No more than 5 SQL Statements should be executed in any given transaction". The rules and also the transactions that these rules are
verified against are defined in a rules file. As an example see the archivalrules.xml file from the Sample Package.  
Following Ant Target executes the rules and creates a resulting XML file:

    
    
    <target name="ArchitecturValidation">
      <DtArchiVal source="live:GoSpace" archiValFile="archivalrules.xml" reportFile="./results/archivalreport.xml" errorProperty="ArchiValFailed"/>
    </target>

A detailed description of this feature will follow shortly

