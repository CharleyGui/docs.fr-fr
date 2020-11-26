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
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Procédure : créer un service qui accepte des données arbitraires à l’aide du modèle de programmation REST WCF

Les développeurs doivent parfois avoir le contrôle total de la manière dont les données sont retournées à partir d'une opération de service. C’est le cas lorsqu’une opération de service doit retourner des données dans un format non pris en charge byWCF. Cette rubrique décrit l’utilisation du modèle de programmation REST WCF pour créer un service qui reçoit des données arbitraires.  
  
### <a name="to-implement-the-service-contract"></a>Pour implémenter le contrat de service  
  
1. Définition du contrat de service. L'opération qui reçoit les données arbitraires doit avoir un paramètre de type <xref:System.IO.Stream>. De plus, ce paramètre doit être le seul paramètre passé dans le corps de la demande. L'opération décrite dans cet exemple prend également un paramètre de nom de fichier. Ce paramètre est passé dans l'URL de la demande. Vous pouvez préciser qu'un paramètre soit passé dans l'URL en spécifiant un <xref:System.UriTemplate> dans <xref:System.ServiceModel.Web.WebInvokeAttribute>. Dans ce cas, l’URI utilisé pour appeler cette méthode se termine par « UploadFile/some-filename ». La partie « {filename} » du modèle URI spécifie que le paramètre de nom de fichier pour l’opération est passé dans l’URI utilisé pour appeler l’opération.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Implémentez le contrat de service. Le contrat a une seule méthode, `UploadFile`, qui reçoit un fichier de données arbitraires dans un flux de données. L'opération lit le flux de données en comptant le nombre d'octets lus, puis affiche le nom de fichier et ce nombre.  
  
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
  
### <a name="to-host-the-service"></a>Pour héberger le service  
  
1. Créez une application console pour héberger le service.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. Créez une variable pour stocker l'adresse de base du service dans la méthode `Main`.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Créez une instance <xref:System.ServiceModel.ServiceHost> pour le service qui spécifie son adresse de base et sa classe.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. Ajoutez un point de terminaison qui spécifie le contrat, <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Ouvrir l'hôte de service. Le service est prêt à recevoir des demandes.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Pour appeler le service par programme  
  
1. Créez un <xref:System.Net.HttpWebRequest> avec l'URI utilisé pour appeler le service. Dans ce code, l'adresse de base est combinée avec `"/UploadFile/Text"`. La partie `"UploadFile"` de l'URI spécifie l'opération à appeler. La partie `"Test.txt"` de l'URI spécifie le paramètre de nom de fichier à passer à l'opération `UploadFile`. Ces deux éléments sont mappés au <xref:System.UriTemplate> appliqué au contrat de l'opération.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. Affectez <xref:System.Net.HttpWebRequest.Method%2A> à la propriété <xref:System.Net.HttpWebRequest> de `POST` et la propriété <xref:System.Net.HttpWebRequest.ContentType%2A> à `"text/plain"`. Cela indique au service que le code envoie des données qui sont au format texte brut.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. Appelez <xref:System.Net.HttpWebRequest.GetRequestStream%2A> pour obtenir le flux de requête, créez les données à envoyer, écrivez ces données dans le flux de requête, puis fermez ce dernier.  
  
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
  
4. Obtenez la réponse du service en appelant <xref:System.Net.HttpWebRequest.GetResponse%2A> et affichez les données de réponse à la console.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Fermez l'hôte de service.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a> Exemple  

 L'intégralité du code utilisé dans cet exemple est présentée ci-dessous.  
  
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
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Lors de la compilation du code, faites référence à System.ServiceModel.dll et System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Voir aussi

- [UriTemplate et UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Modèle de programmation HTTP Web WCF](wcf-web-http-programming-model.md)
- [Vue d'ensemble du modèle de programmation Web HTTP WCF](wcf-web-http-programming-model-overview.md)
