---
title: 'Procédure : créer un service qui accepte des données arbitraires à l’aide du modèle de programmation REST WCF'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: 9c9899705861cc1cf2cda2559c30a0a60d8cc635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237831"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="d4fc7-102">Procédure : créer un service qui accepte des données arbitraires à l’aide du modèle de programmation REST WCF</span><span class="sxs-lookup"><span data-stu-id="d4fc7-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>

<span data-ttu-id="d4fc7-103">Les développeurs doivent parfois avoir le contrôle total de la manière dont les données sont retournées à partir d'une opération de service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="d4fc7-104">C’est le cas lorsqu’une opération de service doit retourner des données dans un format non pris en charge byWCF.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="d4fc7-105">Cette rubrique décrit l’utilisation du modèle de programmation REST WCF pour créer un service qui reçoit des données arbitraires.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="d4fc7-106">Pour implémenter le contrat de service</span><span class="sxs-lookup"><span data-stu-id="d4fc7-106">To implement the service contract</span></span>  
  
1. <span data-ttu-id="d4fc7-107">Définition du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-107">Define the service contract.</span></span> <span data-ttu-id="d4fc7-108">L'opération qui reçoit les données arbitraires doit avoir un paramètre de type <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="d4fc7-109">De plus, ce paramètre doit être le seul paramètre passé dans le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="d4fc7-110">L'opération décrite dans cet exemple prend également un paramètre de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="d4fc7-111">Ce paramètre est passé dans l'URL de la demande.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="d4fc7-112">Vous pouvez préciser qu'un paramètre soit passé dans l'URL en spécifiant un <xref:System.UriTemplate> dans <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="d4fc7-113">Dans ce cas, l’URI utilisé pour appeler cette méthode se termine par « UploadFile/some-filename ».</span><span class="sxs-lookup"><span data-stu-id="d4fc7-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="d4fc7-114">La partie « {filename} » du modèle URI spécifie que le paramètre de nom de fichier pour l’opération est passé dans l’URI utilisé pour appeler l’opération.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="d4fc7-115">Implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-115">Implement the service contract.</span></span> <span data-ttu-id="d4fc7-116">Le contrat a une seule méthode, `UploadFile`, qui reçoit un fichier de données arbitraires dans un flux de données.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="d4fc7-117">L'opération lit le flux de données en comptant le nombre d'octets lus, puis affiche le nom de fichier et ce nombre.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="d4fc7-118">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="d4fc7-118">To host the service</span></span>  
  
1. <span data-ttu-id="d4fc7-119">Créez une application console pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="d4fc7-120">Créez une variable pour stocker l'adresse de base du service dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="d4fc7-121">Créez une instance <xref:System.ServiceModel.ServiceHost> pour le service qui spécifie son adresse de base et sa classe.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="d4fc7-122">Ajoutez un point de terminaison qui spécifie le contrat, <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="d4fc7-123">Ouvrir l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-123">Open the service host.</span></span> <span data-ttu-id="d4fc7-124">Le service est prêt à recevoir des demandes.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="d4fc7-125">Pour appeler le service par programme</span><span class="sxs-lookup"><span data-stu-id="d4fc7-125">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="d4fc7-126">Créez un <xref:System.Net.HttpWebRequest> avec l'URI utilisé pour appeler le service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="d4fc7-127">Dans ce code, l'adresse de base est combinée avec `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="d4fc7-128">La partie `"UploadFile"` de l'URI spécifie l'opération à appeler.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="d4fc7-129">La partie `"Test.txt"` de l'URI spécifie le paramètre de nom de fichier à passer à l'opération `UploadFile`.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="d4fc7-130">Ces deux éléments sont mappés au <xref:System.UriTemplate> appliqué au contrat de l'opération.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="d4fc7-131">Affectez <xref:System.Net.HttpWebRequest.Method%2A> à la propriété <xref:System.Net.HttpWebRequest> de `POST` et la propriété <xref:System.Net.HttpWebRequest.ContentType%2A> à `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="d4fc7-132">Cela indique au service que le code envoie des données qui sont au format texte brut.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="d4fc7-133">Appelez <xref:System.Net.HttpWebRequest.GetRequestStream%2A> pour obtenir le flux de requête, créez les données à envoyer, écrivez ces données dans le flux de requête, puis fermez ce dernier.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4. <span data-ttu-id="d4fc7-134">Obtenez la réponse du service en appelant <xref:System.Net.HttpWebRequest.GetResponse%2A> et affichez les données de réponse à la console.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="d4fc7-135">Fermez l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="d4fc7-136"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d4fc7-136">Example</span></span>  

 <span data-ttu-id="d4fc7-137">L'intégralité du code utilisé dans cet exemple est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-137">The following is a complete listing of the code for this example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d4fc7-138">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d4fc7-138">Compiling the Code</span></span>  
  
- <span data-ttu-id="d4fc7-139">Lors de la compilation du code, faites référence à System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="d4fc7-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fc7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4fc7-140">See also</span></span>

- [<span data-ttu-id="d4fc7-141">UriTemplate et UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d4fc7-141">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="d4fc7-142">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="d4fc7-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="d4fc7-143">Vue d'ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d4fc7-143">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
