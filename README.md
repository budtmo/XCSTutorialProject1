Simple iOS application 
======================

Requirements
------------
1. XOS 10.11 or higher
2. Xcode 7 or higher
3. [xcpretty] - create test result in xml format 
	
	```
	gem install xcpretty
	```

4. [slather] - create test coverage in xml format
	
	```
	gem install slather
	```

Quick Start
-----------
1. Clone the project

	```
	git clone git@github.com:butomo1989/XCSTutorialProject1.git
	```

2. Navigate to project

	```
	cd XCSSampleProject
	```

Execution of UI-Tests
---------------------
### From IDE:
1. open the project

	```
	open XCSTutorialProject1.xcodeproj
	```

2. select scheme, target device and then click 'run test' icon
	
	![][IDE]

### From command line
1. run command 
	
	```
	xcodebuild test -project <xcode-project> -scheme <scheme> -destination <target-device> | xcpretty -s -r <report-type> --output <report-file> && slather
	```

	example:

	```
	xcodebuild test -project XCSTutorialProject1.xcodeproj -scheme XCSTutorialProject1 -destination 'name=iPhone 7,OS=10.2' | xcpretty -s -r junit --output report-junit.xml && slather
	```

Publish test result in Jenkins
------------------------------

![][test result]

![][test coverage]

How to zip to .ipa file
-----------------------

1. Open the project in Xcode

	```
	open XCSTutorialProject1.xcodeproj
	```
	
2. Rename Bundle Identifier in Identity section

3. Select team in Signing section. (If there is no Apple ID stored there, log in with your Apple ID)

4. Select Product -> Build For -> Running

5. Go to build directory

6. Create a new directory named "Payload"
	
	```
	mkdir Payload
	```

7. Move app folder into "Payload"

	```
	cp -r sample.app Payload
	```
	
8. Zip the "Payload" into .ipa 

	```
	zip -r final_app.ipa Payload/
	```
	
Source: [zip tutorial]
	
[IDE]: <images/how_to_run.png>
[xcpretty]: <https://github.com/supermarin/xcpretty>
[slather]: <https://github.com/SlatherOrg/slather>
[test result]: <images/test_result.png>
[test coverage]: <images/test_coverage.png>
[zip tutorial]: <https://github.com/awslabs/aws-device-farm-sample-app-for-ios>
