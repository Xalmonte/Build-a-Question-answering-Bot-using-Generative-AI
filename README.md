# Build-a-Question-answering-Bot-using-Generative-AI

## AWS services used

1. AWS Cloud9
2. Amazon SageMaker
3. Amazon Kendra
4. Amazon Lex v2
5. AWS CloudFormation
6. AWS Lambda
7. AWS CodeBuild

## Step by step Instructions

1. On the AWS Console, start by searching and choosing SageMaker

2. On the left hand side, under Inference, choose Endpoint configurations

3. I chose sagemaker-flan-Endpointconfig.

4. Scroll down to variants section  to ensure it has been deployed (lab ready)

5. On the left hand side, under Inference, choose Endpoints again and confirm that QuestionAnswerBotEndPoint is listed as InService

6. I opened a new browser and on the AWS Console, I searched and chose Kendra

<img width="1438" alt="step 1" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/882e9460-8e81-413b-b70d-7900ee9713ed">


7. Select Index and select add data sources and I uploaded a large dataset already provided for the lab.

<img width="1438" alt="Step 2" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/2d9f6ac3-a55a-4ecf-8356-b9dc996f4029">

8. I was brought to a define attributes page
   
 <img width="1438" alt="step 3" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/c9f8f0c2-a7f4-456c-9f91-63ce54d528c8">


 9. I named the data source,provided description details, confirmed that the language was set to English and chose add data source at the bottom.

     <img width="1438" alt="step 4" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/c491b999-f2e8-4245-97ca-ce5200fbf7d7">

10. In the data source details section, I located the Data source ID which confirmed that the Amazon S3 connector was used to add documentation to my index.

<img width="1438" alt="step 5" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/e1854989-aa0d-4d83-bafa-cb74f22d7b74">


11. I headed back to the AWS Console and searched for Lex. I then selected create bot button.

<img width="1438" alt="step 6" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/c27ff46f-a810-443d-9f99-c1aed5fde51c">



12. I Selected create a blank bot, gave it a name of QuestionAnswerBot, as well as a description.
    
    <img width="1438" alt="step 7" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/444b5246-01b7-4aa2-a573-75cf07e1b257">

13. I scrolled down and in the IAM Permissions section, I chose Use an existing role which I selected the lab made role and selected No under "Is use of your bot subject to the Children's Online Privacy Protection Act" section. 

    <img width="1438" alt="step 8" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/1df323fb-71c0-4149-acde-a8de1cfb5aca">


14.    Select next at the bottom, leave the next page in it's default settings then select done (step not shown).


15. In the NewIntent page, under Intent details, I changed the name to RequiredIntent.


<img width="1438" alt="step 9" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/049d2218-8f0f-48d9-9141-7d1348d8629d">


16. I scrolled down to Sample Utterances section, chose the plain text button and entered Required utterance in the text box followed by save intent.

<img width="1438" alt="step 10" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/5518b00e-193e-4673-aacb-1c072c029bc5">


17. Next, navigate back to intents list which should now show 2 intents and select Add intent.

    <img width="1438" alt="step 11" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/fd5e9b39-05a3-4077-963d-c8b4da306266">

18. I used the attached information below to add my next intent followed by add to add the intent:

<img width="1438" alt="step 12" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/f5228801-4663-4a9c-9e1e-4416b1432a89">

19.  I scrolled down to the Closing response section and in the Message group section, I entered the following Information follow by save intent at the bottom of the screen:

  <img width="1438" alt="step 13" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/d1555a28-c732-44ef-bc58-66dc09bfd124">


20. Now I scrolled to the top of the screen and selected build. Once the bot was built, I chose test and used the following prompts to test the bot:

   <img width="1438" alt="step 14" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/615891a2-a9fe-4c45-aea7-e0cc664091e7">

<img width="1438" alt="step 14 pt  2" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/13820c86-8bce-4dce-94e8-059c00abe1ba">

21. In this next step, we want to connect an AWS Cloud9 Environment to build the Docker Image and Push it to ECR.


22.  I went into a link provided by AWS to log into Cloud9, "x" everything out and used the + button and selected New Terminal.

<img width="1438" alt="step 15" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/fec05c66-0629-4352-9662-61f82e1c2133">

23. I typed the following command to navigate to the builddir directory and view the files that have been saved.

   <img width="1438" alt="step 16" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/ef5d9703-6286-4232-b279-84d9fdb5ae30">

24. I used the following command to set the environment variables for my AWS Region and Account ID:

<img width="1438" alt="step 17" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/6d66baeb-bd2a-495d-b4ab-443819250ed4">

25. I used the following command to save the ID of my Kendra Index to an environment variable:

<img width="1438" alt="step 18" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/1a8d016e-beeb-4a50-9f49-62b71e0c910f">

 26. I entered the following command to save the name of my FLAN T5 XL endpoint to an environment variable:

<img width="1438" alt="step 19" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/061f6983-7def-4f4b-93cd-85af07d9c1bb">

27. I entered the following command to create a Dockerfile for the Lambda function:

<img width="1438" alt="step 20" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/c375dc57-46e0-4095-8307-7b59be806568">

    
28. I typed the following command to build my Docker Image:

  <img width="1438" alt="step 21" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/a83df4f3-55fb-48ac-ab97-b1a344591bef">


29. I entered the following command to create a new ECR repository for my Image:

<img width="1438" alt="step 22" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/01eb522e-fde4-45ba-b3e3-5d3a9f5b64a3">

30. I entered the following command to tag my Image and push it to the newly created repository:

    <img width="1438" alt="step 23" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/0f426ecf-2912-4547-bb6a-5dd424c8158f">

31. After I pushed the image to ECR, I went back to the AWS Console, searched and chose Lambda, and chose the create function button.

   <img width="1438" alt="step 24" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/994278a6-5698-42a1-a560-370503b0710e">

32. At the top of the function screen, I selected Container Image, entered "RAGKendraLLMLexOrchestrator" as the name, selected browse images for my Container Image URL which I then chose rag-kendra-llm-lex, selected the radio button next to the latest and chose the select image button.

    
<img width="1438" alt="step 25" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/3d05a116-2e32-470a-b9e3-f9b322066a2a">

33. Leave the remaining Information the same and chose create function at the bottom.

<img width="1438" alt="step 26" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/0cd6791b-0c57-4606-94cc-7952e4051af6">

34. I was brought to the RagKendraLLMLexOrchestrtor page after I created the function. I scrolled down and chose the configuration tab followed by the edit button.

<img width="1438" alt="step 27" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/9db8c40e-1eb8-4e53-a5f8-0ee97b65ece5">

35. Scroll down and change the Lambda function Timeout to 1 minute followed by save.

         <img width="1438" alt="step 28" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/3cdc3dda-62cd-4b8f-8f8b-1fa414b1f06d">

36. I went back to the AWS Console and searched for IAM

    <img width="1438" alt="step 29" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/2dbff0d9-1299-463d-8b7a-ee026644a5b7">

37.   In the search bar, I typed "RAGKendraLLMLexOrchestrator" to locate the role created for the function. I then chose the role.

<img width="1438" alt="step 30" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/64e60d7e-eec9-4051-ae03-a1176643a7ee">

38. I scrolled to the bottom of the page to the Permissions policies section, selected "Add Permissions" and selected attach policies

<img width="1438" alt="step 31" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/7f17d487-e092-4e58-89db-c228fc76afef">

39. In the search bar, I entered "WebAppPolicy," selected the checkbox and chose add permissions.

   <img width="1438" alt="step 32" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/30ae4e66-2170-4e87-803a-9fc68284185e">

40. I should now see two policies attached

    <img width="1438" alt="step 33" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/bc532e20-965f-4847-91a6-4bbaf71a71f1">

41. On the AWS Console, Search and Choose S3. Then I chose the bucket that starts with lex-json-config.

    <img width="1438" alt="step 34" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/d840eaf4-58c2-41a8-ac9a-a122788f2642">

42. I selected the checkbox next to LexConfig.zip and chose the download button.

    <img width="1438" alt="step 35" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/2e7178ed-6811-4380-a138-4aa9a0d2c4cd">

43. I navigated back to Lex from the AWS Console and in the Bots section, I opened the "Action" button and selected Import

    <img width="1438" alt="step 36" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/86900f4b-05e0-4717-9a61-d11cecad9521">

44. I gave the Bot the name of WebAppBot followed by uploading the LexConfig.zip file I downloaded earlier.

<img width="1438" alt="step 37" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/b16a5cbc-f734-44b6-8c58-c000c338d251">

45. In the IAM Permissions section, I chose create a role with basic Amazon Lex Permissions, selected no under the "Is use of your bot subject to the Children's Online Privacy Protection Act" section followed by Import at the bottom of the page.

        <img width="1438" alt="step 38" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/3d0f7062-225a-40ed-83de-185dd6e4d4bb">

46. In the Bot details page, I copied the value next to ID and pasted it to a text editor app in which I'll use at a later step.

   <img width="1438" alt="step 39" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/fb62613b-c3e6-413d-8c93-ec6b62f4ee7c">

47. Now that the Bot has been Imported, it's time to build the Web app. On the AWS Console, I navigated to Cloudformation, selected create stack, and selected with new resources (Standard).

     <img width="1438" alt="step 40" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/0e6f45f0-a5e6-4919-a407-8ee3aa7c7aa9">

48. Under the Specify stack details page, I entered the following details:

    <img width="1438" alt="step 41" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/eb433e02-3d3b-43eb-a6da-b86d55f4ae4c">

49. I scrolled to the bottom of the page and selected the next button which will bring you to another page. Leave that page with it's default settings and I chose the next bottom at the bottom of the screen. I acknowledged the two checkboxes at the end of the page followed by submit.

    <img width="1438" alt="step 42" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/28b6b635-2c9a-499a-a5ee-7eb7a040ef4f">

50. We now have to wait about 10 minutes to wait for the 3 nested stacks to finish building. Once confirmed, I headed to the AWS Console and searched and chose CodeBuild.

    <img width="1438" alt="step 43" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/f5a6b621-86a8-4230-9569-313b0ce42e61">

51. I chose lex-web-ui-kk-RAG-Test and scrolled to the bottom of the page and chose the Build history tab to confirm both builds are listed as succeeded

    <img width="1438" alt="step 44" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/0513f182-05ed-49df-a0fd-b13750046381">

52. Now that we have confirmed this Information, In the AWS Console, search for and choose Lex.

    <img width="1438" alt="step 45" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/1f96072c-3185-43bb-9814-19fed044035e">


53. I scrolled down to the WebAppBot page and located the Create versions and aliases for deployment section. choose the "view aliases" button.

    <img width="1438" alt="step 46" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/e3d4e6da-7ce7-479a-ae31-365c7babed80">

54. I selected the alias you see already created called TestBotAlias

    <img width="1438" alt="step 47" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/335d4a54-5d88-4853-b9ca-47d594db3533">

55. Scroll down to the languages and choose the English(US)

    <img width="1438" alt="step 48" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/66f7f55a-20ff-422f-99de-ae400e6f0955">

56. Select the Information as you see below, ensure that the Lambda function version or alias is set to $Latest and I chose save:

    <img width="1438" alt="step 49" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/379039a5-13b9-4b6c-af1b-7417bd137f43">

57. Click on the LexWebApp and select view languages

    <img width="1438" alt="step 50" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/5bbed454-020f-4bce-b9b4-311413f6fe67">


58. Choose English(US) follow by build on the next screen.

    <img width="1438" alt="step 51" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/8010004b-bfa5-4ade-bb02-a43041a55754">

59. Once it finished building, I naviagted back to Cloudformation and chose LexWebApp. I opened the Outputs tab, scrolled to the bottom of the screen and chose the URL next to the WebAppUrl to launch my Web app. I ran the following commands to confirm the bot was working properly.

    <img width="1438" alt="step 52" src="https://github.com/Xalmonte/Build-a-Question-answering-Bot-using-Generative-AI/assets/169603464/bbdfbefb-b141-43f6-a4e7-eb2e34dedfff">
