# SmartTest
When developer changes the source code, automatically generated the list of test cases to be tested for this change.

# Priciple
To find the recommended tests, you must first run the full test for collecting the association between the changed source code and the impacted test cases.     
   
Once the association created, we can store it in the file/database to facilitate the further query, and generated it every day in CI to keep the data up to date.
   
The association is only collected when tests run and pass. This creates a baseline to gather valid data for which methods are used when the full test is run. When a test fails, only partial data of the methods that were used to run the test could be collected. This partial data would be inaccurate.    
   
Next, any code changes checked in using version control are compared with the association, then, we can get the recommened tests.

# Scope
The test cases must be made in one of the following ways:
- unittest/nosetests
- robot framework

# Execute
Based on nose:    
nosetests --with-smart-test /test_path

Based on robot framework:    
robot --listener smart_test.SmartTestListener /test_path
