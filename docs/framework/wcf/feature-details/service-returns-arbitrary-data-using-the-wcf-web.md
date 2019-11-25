---
title: "Procédure : créer un service qui retourne des données arbitraires à l'aide du modèle de programmation Web HTTP WCF"
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 41d9f0e53401bcd6b57b04a38e76af5ddb9fb4cc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976099"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="a01fe-102">Procédure : créer un service qui retourne des données arbitraires à l'aide du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="a01fe-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="a01fe-103">Les développeurs doivent parfois avoir le contrôle total de la manière dont les données sont retournées à partir d'une opération de service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="a01fe-104">C’est le cas lorsqu’une opération de service doit retourner des données dans un format non pris en charge par WCF.</span><span class="sxs-lookup"><span data-stu-id="a01fe-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="a01fe-105">Cette rubrique décrit l’utilisation du modèle de programmation HTTP WEB WCF pour créer un tel service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="a01fe-106">Ce service a une opération qui retourne un flux de données.</span><span class="sxs-lookup"><span data-stu-id="a01fe-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="a01fe-107">Pour implémenter le contrat de service</span><span class="sxs-lookup"><span data-stu-id="a01fe-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="a01fe-108">Définition du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-108">Define the service contract.</span></span> <span data-ttu-id="a01fe-109">Le contrat est appelé `IImageServer` et a une méthode appelée `GetImage` qui retourne un <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="a01fe-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="a01fe-110">Étant donné que la méthode retourne un <xref:System.IO.Stream>, WCF suppose que l’opération a un contrôle total sur les octets retournés par l’opération de service et qu’elle n’applique aucune mise en forme aux données retournées.</span><span class="sxs-lookup"><span data-stu-id="a01fe-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="a01fe-111">Implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-111">Implement the service contract.</span></span> <span data-ttu-id="a01fe-112">Le contrat a une seule opération (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="a01fe-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="a01fe-113">Cette méthode génère une image bitmap, puis l'enregistre dans un <xref:System.IO.MemoryStream> au format .jpg.</span><span class="sxs-lookup"><span data-stu-id="a01fe-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="a01fe-114">L'opération retourne ensuite ce flux de données à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a01fe-114">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="a01fe-115">Observez l'avant-dernière ligne de code : `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="a01fe-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="a01fe-116">Cela affecte à l’en-tête de type de contenu la valeur `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="a01fe-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="a01fe-117">Bien que cet exemple indique comment retourner un fichier .jpg, il peut être modifié pour retourner tout type de données requis, dans n'importe quel format.</span><span class="sxs-lookup"><span data-stu-id="a01fe-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="a01fe-118">L'opération doit extraire ou générer les données, puis les écrire dans un flux de données.</span><span class="sxs-lookup"><span data-stu-id="a01fe-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="a01fe-119">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="a01fe-119">To host the service</span></span>  
  
1. <span data-ttu-id="a01fe-120">Créez une application console pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2. <span data-ttu-id="a01fe-121">Créez une variable pour stocker l'adresse de base du service dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="a01fe-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="a01fe-122">Créez une instance <xref:System.ServiceModel.ServiceHost> pour le service spécifiant son adresse de base et sa classe.</span><span class="sxs-lookup"><span data-stu-id="a01fe-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="a01fe-123">Ajoutez un point de terminaison à l'aide de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a01fe-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="a01fe-124">Ouvrir l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="a01fe-125">Patientez jusqu'à ce que l'utilisateur appuie sur ENTRÉE pour arrêter le service.</span><span class="sxs-lookup"><span data-stu-id="a01fe-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="a01fe-126">Pour appeler le service brut à l'aide d'Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="a01fe-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="a01fe-127">Exécutez le service. La sortie suivante devrait apparaître.</span><span class="sxs-lookup"><span data-stu-id="a01fe-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="a01fe-128">Ouvrez Internet Explorer et tapez `http://localhost:8000/Service/GetImage?width=50&height=40`. Un rectangle jaune traversé en son centre par une ligne diagonale bleue devrait apparaître.</span><span class="sxs-lookup"><span data-stu-id="a01fe-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01fe-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="a01fe-129">Example</span></span>  
 <span data-ttu-id="a01fe-130">L'intégralité du code utilisé dans cette rubrique est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a01fe-130">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a01fe-131">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a01fe-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="a01fe-132">Lors de la compilation de l'exemple de code, faites référence à System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="a01fe-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01fe-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a01fe-133">See also</span></span>

- [<span data-ttu-id="a01fe-134">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="a01fe-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
