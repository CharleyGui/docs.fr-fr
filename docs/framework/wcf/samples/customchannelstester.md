---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 0d77af319e18868ce7d600269cd9afaa0c4ce2c6
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928642"
---
# <a name="customchannelstester"></a><span data-ttu-id="bf7b2-102">CustomChannelsTester</span><span class="sxs-lookup"><span data-stu-id="bf7b2-102">CustomChannelsTester</span></span>
<span data-ttu-id="bf7b2-103">`CustomChannelsTester` est un outil utilisé pour tester vos implémentations de canal personnalisées sur un jeu de contrats de service prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-103">The `CustomChannelsTester` is a tool that you can use to test your custom channel implementations against a set of predefined service contracts.</span></span> <span data-ttu-id="bf7b2-104">Vous pouvez sélectionner le jeu de contrats de service et le transmettre à l'outil à l'aide d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-104">You can select the set of service contracts and pass it to the tool using an XML file.</span></span> <span data-ttu-id="bf7b2-105">L'outil génère ensuite le service et le client qui effectue vos implémentations de canal personnalisées pendant l'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-105">The tool then generates the service and client that exercises your custom channel implementations during message exchange.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="bf7b2-106">Pour générer l'outil</span><span class="sxs-lookup"><span data-stu-id="bf7b2-106">To build the tool</span></span>  
  
1. <span data-ttu-id="bf7b2-107">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b2-107">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="bf7b2-108">La génération de la solution crée trois fichiers : CustomChannelsTester.exe, TestSpec.xml et SampleRun.cmd. CustomChannelsTester.exe, TestSpec.xml et SampleRun.cmd.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-108">Building the solution generates three files: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd.</span></span> <span data-ttu-id="bf7b2-109">Le fichier SampleRun. cmd contient un exemple de ligne de commande qui montre comment utiliser cet outil pour tester [le transport : Exemple](../../../../docs/framework/wcf/samples/transport-udp.md) UDP.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-109">The file SampleRun.cmd has a sample command line that shows how to use this tool to test the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="bf7b2-110">Pour exécuter l'outil</span><span class="sxs-lookup"><span data-stu-id="bf7b2-110">To run the tool</span></span>  
  
- <span data-ttu-id="bf7b2-111">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7b2-111">At the command prompt type the following command:</span></span>  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     <span data-ttu-id="bf7b2-112">L'utilisation de l'option `/binding` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-112">Using the `/binding` option is required.</span></span>  
  
     <span data-ttu-id="bf7b2-113">`/dll`est requis si la « liaison » n’est pas une liaison fournie par le système fournie par Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf7b2-113">`/dll` is required if "binding" is not a system-provided binding provided by Windows Communication Foundation (WCF).</span></span>  
  
     <span data-ttu-id="bf7b2-114">`/testspec` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-114">`/testspec` is optional.</span></span>  
  
     <span data-ttu-id="bf7b2-115">Cela crée le serveur et les clients basés sur les caractéristiques de test et la liaison.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-115">This creates server and clients based on the test specifications and the binding.</span></span>  
  
     <span data-ttu-id="bf7b2-116">Exécute le client et le serveur, et retourne les résultats.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-116">Executes the client and server and returns the results.</span></span>  
  
     <span data-ttu-id="bf7b2-117">Voici l'exemple XML pour la description des caractéristiques de test (testspec.xml) :</span><span class="sxs-lookup"><span data-stu-id="bf7b2-117">The following is the sample XML for the description of the test specifications (testspec.xml):</span></span>  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
