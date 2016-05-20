## AWS Lambda function for Alexa & FunnyQuoter
A sample [AWS Lambda](http://aws.amazon.com/lambda) function that demonstrates the following use cases for FunnyQuoter

* Funny Quoter is here to make you smile with dozens of funny quotes. 
* Just ask Alexa, and laugh aloud while real people spout hilarious one-liners!

## Examples 
"Alexa, ask Funny Quoter to tell me a quote."

"Alexa, tell Funny Quoter to make me smile."

"Alexa, tell Funny Quoter to cheer me up."


## Setup
To run this FunnyQuoter skill you need to do two things. The first is to deploy the skill code in lambda and configure the Alexa skill to use Lambda
 
### AWS Lambda Setup
1.	Go to the [AWS Console](http://console.aws.amazon.com) and click on the Lambda link. Note: ensure you are in us-east or you won't be able to use Alexa with Lambda.
2.	Click on the Create a Lambda Function or Get Started Now button.
3.	Name the Lambda Function "FunnyQuoter".
4.	Go to the the src directory, select all files and folders and then create a zip file, make sure the zip file does not contain the src directory itself, otherwise Lambda function will not work.
5.	Upload the .zip file to the Lambda 
6.	Select the Runtime as Node.js 4.3
7.	Keep the Handler as index.handler (this refers to the main js file in the zip).
8.	Select role as alexa and keep other configuration as it is.
9.	Return to the main Lambda page, and click on "Events Sources" tab and click "Add Event Source".
10.	Choose Alexa Skills Kit and click submit.
11.	Copy the ARN from the upper right to be used later in the Alexa Skill Setup

### Alexa Skill Setup

1. Go to the [Alexa Developer Console](https://developer.amazon.com/edw/home.html) and click Add a New Skill.
2. Select Skill Type *Custom Interaction Model*
3. Set "Funny Quoter" as the skill name and "funny quoter" as the invocation name, this is what is used to activate your skill. For example you would say: "Alexa, ask Funny Quoter to tell me a quote. " Click Next.
4. Copy the Intent Schema from the included file speechAssets/IntentSchema.json.
5. Copy the Sample Utterances from the included file speechAssets/SampleUtterances.txt. Click Next.
6. Select the Lambda ARN for the skill Endpoint and paste the ARN copied from above. 
7. Select *Account Linking* to *No*. Click Next.
8. Go back to the skill Information tab and copy the appId. Paste the appId into the index.js file for the variable APP_ID, then update the lambda source zip file with this change and upload to lambda again, this step makes sure the lambda function only serves request from authorized source.
9. Add you audio file paths in array audioPathArray in the index.js file. Preference to store audio file should be on amazon s3. Audio should have public read access.  
10. You are now able to start testing your sample skill! You should be able to go to the [Echo webpage](http://echo.amazon.com/#skills) and see your skill enabled.
11. Your skill is now saved and once you are finished testing you can continue to publish your skill.
