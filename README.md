### This is a personal documentation for deploying an Angular frontend and .NET core API backend app to azure and integrating CICD
<br>

First i have created a repo in azure devops where my angular and .net code will be pushed.Later i will publish my app using azure serices and will integrate CI/CD.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/ba9a8254-2bbc-4586-80b9-f8a50d93a981) | 
|:--:| 
| *Azure repo containg two branches, master one is using for backend code while other one is using for frontend* |

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/4e7b441a-a2c7-473a-a7f3-b1acdf3f2a82) | 
|:--:| 
| *API branch in azure repo and will publish it using azure app service* |


| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/db31f5cc-e8ae-464c-8efa-6bd98cea8306) | 
|:--:| 
| *angular app branch in azure repo and will publish it using azure static web app* |
<br>

now in azure portal will create one app service where API and db will be deployed. i will use azure sql for db. 

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/fa68434b-6974-4bc8-9340-1e6bb3846a52) | 
|:--:| 
| *app service created and inside configuration section of app service we can find db configuration* |

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/91cad450-db91-4f73-8da6-e1d778d2708c) | 
|:--:| 
| *expand this variable to see detailed connection string* |

now i have taken db connection string from configuration section and used in in backend service before dploying to azure.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/874da372-3961-4c43-b812-ad798b90e67c) | 
|:--:| 
| *connected to azure sql db from local and migrated db* |

now i created one more service in azure to publish angular app using azure static web app. reason behind choosing static web app over web service was as it's comperatively faster and cheaper. also can handle authentication, authorization. also later i planned to convert backend into azure functions so all of these resons were behind choosing that.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/63450ba8-fb0d-4ea7-9cee-040b8232708e) | 
|:--:| 
| *created azure static web app to deploy angular app* |

now azure services are ready . will configure pipeline to my repo. for creating pipeline i have used classic editor. i will convert it to yaml later as it has more flexibility.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/ee3d89c6-be48-4b65-a62c-ee666c860eab) | 
|:--:| 
| *Build pipeline for .NET API backend* |

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/36c24d2c-4b66-4889-ae0d-def7c477ad09) | 
|:--:| 
| *Build pipeline for Angular frontend* |

Build pipeline created. althought currently i dont have any unit test project to test my app so i diabled test step for now.
need to created release pipeline now.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/b5375228-06ae-41d7-8a8f-7a3901445239) | 
|:--:| 
| *Release pipeline for .NET API backend* |

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/05cd0645-423b-49a0-8102-dec3b1e66f7a) | 
|:--:| 
| *Release pipeline for Angular frontend* |

now pushed my code from local env for both front and backend to azure repo and check in azure devops. it should be deployed in azure as already configured CI/CD.

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/e7ad934f-bc6f-407c-b5e9-0be56987cb7f) | 
|:--:| 
| *API hosted on Azure* |

| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/33fd3baf-bbd9-4953-a041-8add36008658) | 
|:--:| 
| *Angular app hosted on Azure* |


| ![space-1.jpg](https://github.com/sadman6259/Azure-CICD-doc/assets/32922365/aba2c5eb-708a-4b7c-b951-2961659a118e) | 
|:--:| 
| *Frontend is calling API fine, can successfully logged in and data retrieved* |
<br>
<br>
THE END !













