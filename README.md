# HPC Skilling Hands-On Exercises
Zero to Batch Module



## Deployment & Use



1.  **Add the Role**

    In Azure Portal, Open the subscription IAM, Which is the subscription you use for installation.

<img src="https://learnmdfiles.blob.core.windows.net/files/image1.png" width="50%"/>
    ![](https://learnmdfiles.blob.core.windows.net/files/image1.png)

    On that IAM page, select "**Add role assignment**" under the Add tab.

    ![](https://learnmdfiles.blob.core.windows.net/files/image2.png)

    In the Role tab, select the "Contributor" role.

    ![](https://learnmdfiles.blob.core.windows.net/files/image3.png)

    In the Member tab, click the "select members" option. Left side, The Select member\'s Panel will open. Select "Microsoft Azure Batch".

    ![](https://learnmdfiles.blob.core.windows.net/files/image4.png)

    After selecting the member click "Review + assign".

    ![](https://learnmdfiles.blob.core.windows.net/files/image5.png)

    ![](https://learnmdfiles.blob.core.windows.net/files/image6.png)

    After Assignment success, you can see the Microsoft Azure batch app under the "Role Assignments" tab

    ![](https://learnmdfiles.blob.core.windows.net/files/image7.png)

2.  **Deploy Virtual Machine**

    Browse the following link:

    <https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fpavithra-terawe%2Fhpc_azfinsim2%2Fmain%2Farmtemplate%2Fenvironment%2Farmtemplate.json>

    Select you login details.

    ![](https://learnmdfiles.blob.core.windows.net/files/image8.png)

    After login, the "Custom deployment" page will open. Select the Resource Group and Change the password if you need. Then create the deployment.

    ![](https://learnmdfiles.blob.core.windows.net/files/image9.png)

3.  **Connect VM**

    Once the virtual machine deployed successfully. Connect to the virtual machine using ssh connectivity with the password.

    Example :ssh deployeradmin@52.149.120.180

    ![](https://learnmdfiles.blob.core.windows.net/files/image10.png)

    ![](https://learnmdfiles.blob.core.windows.net/files/image11.png)

4.  AZ login

    Next, login with the Azure CLI. 

    Example: az login 

    ![](https://learnmdfiles.blob.core.windows.net/files/image12.png)

 

Open the link in the browser and enter the code. 

 

![IMG_256](https://learnmdfiles.blob.core.windows.net/files/image13.png)

 

Click the next button and select the required account to login. 

 

![IMG_257](https://learnmdfiles.blob.core.windows.net/files/image14.png)

 

![](https://learnmdfiles.blob.core.windows.net/files/image15.png)

After login, all available accounts will be listed. 

![](https://learnmdfiles.blob.core.windows.net/files/image16.png)

5.  **Set az account**

Set the az account using the following command. 

Example: az account set -s \<sid\> 

![](https://learnmdfiles.blob.core.windows.net/files/image17.png)

6.  **Clone the repo**

    Clone the following repo into the connected VM.

    Example: git clone <https://github.com/pavithra-terawe/hpc_azfinsim2>

    ![](https://learnmdfiles.blob.core.windows.net/files/image18.png)

7.  **Give the Permission**

    Example: sudo chmod 777 \*

    ls -ltr

    ![](https://learnmdfiles.blob.core.windows.net/files/image19.png)

8.  **Move to Repo**

    Example: cd hpc_azfinsim2/

    ![](https://learnmdfiles.blob.core.windows.net/files/image20.png)

9.  **Requirement python package install**

    To install the requirements python package, do the following command.

    Example: pip install -r src/requirements.txt

    ![](https://learnmdfiles.blob.core.windows.net/files/image21.png)

10. **Move to Bin**

    Example: cd bin/

    ![](https://learnmdfiles.blob.core.windows.net/files/image22.png)

11. **Give the Permission**

    Example: sudo chmod +rx \*

    ls -ltr

    ![](https://learnmdfiles.blob.core.windows.net/files/image23.png)

12. **Deploy Function**

    To deploy, move to the bin folder and run the following command:

    Example: ./deploy.sh

    ![](https://learnmdfiles.blob.core.windows.net/files/image24.png)

    While the deployment running, that will ask the approve. Enter yes to accept.

    ![](https://learnmdfiles.blob.core.windows.net/files/image25.png)

    ![](https://learnmdfiles.blob.core.windows.net/files/image26.png)

13. **Inject function**

    After the deployment is complete, Run the injected script.

    Example: ./inject.sh

    ![](https://learnmdfiles.blob.core.windows.net/files/image27.png)

14. **Build function**

    After inject script is complete, run build script.

    Example: ./build.sh

    ![](https://learnmdfiles.blob.core.windows.net/files/image28.png)

    ![](https://learnmdfiles.blob.core.windows.net/files/image29.png)

15. **Submit function**

    After the build script is completed successfully, run submit function.

    Example: ./submit.sh

    If you get a permission error, move back to the root folder and run the following command.

    Example: cd ..

    sudo chmod 777 src/\*

    ls -ltr src

    ![](https://learnmdfiles.blob.core.windows.net/files/image30.png)

    After that, move to the bin folder and run the submit script.

    Example: ./submit.sh

    ![](https://learnmdfiles.blob.core.windows.net/files/image31.png)

    Output:

    ![](https://learnmdfiles.blob.core.windows.net/files/image32.png)

    After the submit script is completed. You can see the jobs and pool in your deployed environment batch files.

>> ![](https://learnmdfiles.blob.core.windows.net/files/image33.png)

>> ![](https://learnmdfiles.blob.core.windows.net/files/image38.png)

**Viewing Running Jobs(Optional)**

Login into the "Batch Explorer" (download from the browser). If you click on the \"Jobs\" menu in the Batch Explorer UI, you\'ll see the three running jobs there:

![](https://learnmdfiles.blob.core.windows.net/files/image37.png)

16. **Destroy function.**

    If you want to delete your files, run destroy script.

    Example: ./destroy.sh

    ![](https://learnmdfiles.blob.core.windows.net/files/image35.png)

    While the destroy running, that will ask the approval. Enter yes to accept.

    ![](https://learnmdfiles.blob.core.windows.net/files/image36.png)

Output: All the resources are deleted in the resource group.

![](https://learnmdfiles.blob.core.windows.net/files/image39.png)

# Next Steps 

## Securing Azure Batch 

The following are a compilation of **best practices** for securing deployments of Azure Batch:

-   Make use of User Subscription mode

-   Only expose deployed services (e.g., Azure Batch, Azure storage services, Azure Key Vault, ACR, ...) as private endpoints

-   Compute pools should

    -   Only exist in private IP address space

    -   Be deployed as a Managed Identity for ACR interaction

    -   Be separate for development and production resources

    -   Provide external access via a VPN or the Azure Bastion Service -- note that 'jump boxes' can be preinstalled with software for Windows or Linux

-   Implement a firewall

For additional discussion on each of these practices refer to <https://github.com/mocelj/AzureBatch-Secured>.
