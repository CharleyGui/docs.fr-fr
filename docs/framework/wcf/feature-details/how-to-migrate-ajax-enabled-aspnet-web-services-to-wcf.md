---
title: 'Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 1650ba6a12a9e81ff398e66a96ee2c70592f2428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643686"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="73ada-102">Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="73ada-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="73ada-103">Cette rubrique décrit les procédures pour migrer un service de base ASP.NET AJAX à un service compatible AJAX Windows Communication Foundation (WCF) équivalente.</span><span class="sxs-lookup"><span data-stu-id="73ada-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="73ada-104">Il montre comment créer une version WCF fonctionnellement équivalente d’un service ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="73ada-105">Les deux services peuvent ensuite servir côte à côte, ou le service WCF peut être utilisé pour remplacer le service ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="73ada-106">Migration d’ASP.NET AJAX existant service à un service WCF AJAX vous offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="73ada-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="73ada-107">Vous pouvez exposer votre service AJAX en tant que service SOAP avec une configuration supplémentaire minimale.</span><span class="sxs-lookup"><span data-stu-id="73ada-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="73ada-108">Vous pouvez tirer parti des fonctionnalités WCF, telles que le suivi et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="73ada-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="73ada-109">Les procédures suivantes supposent que vous utilisez Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="73ada-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="73ada-110">Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple qui suit les procédures.</span><span class="sxs-lookup"><span data-stu-id="73ada-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="73ada-111">Pour plus d’informations sur l’exposition d’un service WCF via un point de terminaison compatible AJAX, consultez le [Comment : Configuration permet d’ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="73ada-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="73ada-112">Pour créer et tester l'application de service Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73ada-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="73ada-113">Ouvrez Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="73ada-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="73ada-114">À partir de la **fichier** menu, sélectionnez **New**, puis **projet**, puis **Web**, puis sélectionnez **Application de Service Web ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="73ada-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="73ada-115">Nommez le projet `ASPHello` et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="73ada-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="73ada-116">Supprimez les marques de commentaire dans la ligne du fichier Service1.asmx.cs qui contient `System.Web.Script.Services.ScriptService]` pour rendre ce service compatible avec AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="73ada-117">À partir de la **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="73ada-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="73ada-118">Dans le menu **Déboguer**, sélectionnez **Exécuter sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="73ada-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="73ada-119">Sur la page web générée, sélectionnez l’opération `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="73ada-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="73ada-120">Cliquez sur le **Invoke** bouton sur le `HelloWorld` page de test.</span><span class="sxs-lookup"><span data-stu-id="73ada-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="73ada-121">Vous recevez alors la réponse XML suivante.</span><span class="sxs-lookup"><span data-stu-id="73ada-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="73ada-122">Cette réponse confirme que vous bénéficiez désormais d'un service ASP.NET AJAX fonctionnel et, plus précisément, que le service a exposé un point de terminaison à Service1.asmx/HelloWorld qui répond aux requêtes HTTP POST et retourne du code XML.</span><span class="sxs-lookup"><span data-stu-id="73ada-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="73ada-123">Vous êtes maintenant prêt à convertir ce service pour utiliser un service WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="73ada-124">Pour créer une application de service AJAX WCF équivalente</span><span class="sxs-lookup"><span data-stu-id="73ada-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="73ada-125">Avec le bouton droit le **ASPHello** de projet et sélectionnez **ajouter**, puis **un nouvel élément**, puis **Service WCF compatible AJAX**.</span><span class="sxs-lookup"><span data-stu-id="73ada-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="73ada-126">Nommez le service `WCFHello` et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="73ada-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="73ada-127">Ouvrez le fichier WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="73ada-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="73ada-128">À partir de Service1.asmx.cs, copiez l’implémentation suivante de la `HelloWorld` opération.</span><span class="sxs-lookup"><span data-stu-id="73ada-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. <span data-ttu-id="73ada-129">Coller dans une implémentation copiée de le `HelloWorld` opération dans le fichier WCFHello.svc.cs à la place le code suivant.</span><span class="sxs-lookup"><span data-stu-id="73ada-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="73ada-130">Spécifiez le `Namespace` attribut <xref:System.ServiceModel.ServiceContractAttribute> comme `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="73ada-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="73ada-131">Ajouter le <xref:System.ServiceModel.Web.WebInvokeAttribute> à la `HelloWorld` opération et définissez le <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriété à retourner <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="73ada-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="73ada-132">Notez que si la propriété n'est pas définie, le type de retour par défaut est <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="73ada-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="73ada-133">À partir de la **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="73ada-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="73ada-134">Ouvrez le fichier WCFHello.svc et à partir de la **déboguer** menu, sélectionnez **démarrer sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="73ada-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="73ada-135">Le service expose désormais un point de terminaison à `WCFHello.svc/HelloWorld`, qui répond aux requêtes HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="73ada-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="73ada-136">Les requêtes HTTP POST ne peuvent pas être testées à partir du navigateur, mais le point de terminaison retourne le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="73ada-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="73ada-137">Le `WCFHello.svc/HelloWorld` et `Service1.aspx/HelloWorld` points de terminaison désormais sont fonctionnellement équivalents.</span><span class="sxs-lookup"><span data-stu-id="73ada-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="73ada-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="73ada-138">Example</span></span>
 <span data-ttu-id="73ada-139">Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="73ada-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="73ada-140">Le type <xref:System.Xml.XmlDocument> n'est pas pris en charge par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> car il n'est pas sérialisable par <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="73ada-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="73ada-141">Vous pouvez utiliser un type <xref:System.Xml.Linq.XDocument> ou sérialiser <xref:System.Xml.XmlDocument.DocumentElement%2A> à la place.</span><span class="sxs-lookup"><span data-stu-id="73ada-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="73ada-142">Si les services Web ASMX sont mis à niveau et migration côte à côte pour les services WCF, évitez de mapper deux types sur le même nom sur le client.</span><span class="sxs-lookup"><span data-stu-id="73ada-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="73ada-143">Cela provoque une exception dans les sérialiseurs si le même type est utilisé dans un <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.ServiceModel.ServiceContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="73ada-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="73ada-144">Si le service WCF est ajouté en premier, appelant la méthode sur le Service Web ASMX provoque une exception dans <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> parce que la définition de style WCF de l’ordre dans le proxy est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="73ada-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="73ada-145">Si le Service Web ASMX est ajouté en premier, appel de méthode sur un service WCF provoque une exception dans <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> parce que la définition de style de Service Web de l’ordre dans le proxy est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="73ada-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="73ada-146">Il existe des différences de comportement importantes entre le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et le <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="73ada-147">Par exemple, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> représente un dictionnaire sous la forme d'un tableau de paires clé/valeur, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX représente un dictionnaire sous la forme d'objets JSON réels.</span><span class="sxs-lookup"><span data-stu-id="73ada-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="73ada-148">Par conséquent, le code suivant est le dictionnaire représenté dans ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="73ada-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="73ada-149">Ce dictionnaire est représenté dans des objets JSON comme indiqué dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="73ada-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="73ada-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="73ada-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="73ada-151">{« one » : 1, « two » : 2} par ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="73ada-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="73ada-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est plus puissant car il peut gérer des dictionnaires où le type de clé n'est pas une chaîne, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="73ada-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="73ada-153">Cependant, ce dernier est plus compatible avec JSON.</span><span class="sxs-lookup"><span data-stu-id="73ada-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="73ada-154">Les différences principales entre ces sérialiseurs sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="73ada-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="73ada-155">Catégorie de différences</span><span class="sxs-lookup"><span data-stu-id="73ada-155">Category of Differences</span></span>|<span data-ttu-id="73ada-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="73ada-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="73ada-157">JavaScriptSerializer ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="73ada-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="73ada-158">Désérialisation de la mémoire tampon vide (nouvel octet [0]) dans <xref:System.Object> (ou <xref:System.Uri> ou d'autres classes).</span><span class="sxs-lookup"><span data-stu-id="73ada-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="73ada-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="73ada-159">SerializationException</span></span>|<span data-ttu-id="73ada-160">null</span><span class="sxs-lookup"><span data-stu-id="73ada-160">null</span></span>|
|<span data-ttu-id="73ada-161">Sérialisation de <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="73ada-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="73ada-162">{} (ou {« __type » : « #System »})</span><span class="sxs-lookup"><span data-stu-id="73ada-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="73ada-163">Null</span><span class="sxs-lookup"><span data-stu-id="73ada-163">Null</span></span>|
|<span data-ttu-id="73ada-164">Sérialisation des membres privés de types [Sérialisable].</span><span class="sxs-lookup"><span data-stu-id="73ada-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="73ada-165">sérialisée</span><span class="sxs-lookup"><span data-stu-id="73ada-165">serialized</span></span>|<span data-ttu-id="73ada-166">n'est pas sérialisé</span><span class="sxs-lookup"><span data-stu-id="73ada-166">not serialized</span></span>|
|<span data-ttu-id="73ada-167">Sérialisation des propriétés publiques de types <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="73ada-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="73ada-168">n'est pas sérialisé</span><span class="sxs-lookup"><span data-stu-id="73ada-168">not serialized</span></span>|<span data-ttu-id="73ada-169">sérialisée</span><span class="sxs-lookup"><span data-stu-id="73ada-169">serialized</span></span>|
|<span data-ttu-id="73ada-170">« Extensions » de JSON</span><span class="sxs-lookup"><span data-stu-id="73ada-170">"Extensions" of JSON</span></span>|<span data-ttu-id="73ada-171">Respecte la spécification JSON, qui exige des guillemets sur les noms de membres d'objet ({"a":"hello"}).</span><span class="sxs-lookup"><span data-stu-id="73ada-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="73ada-172">Prend en charge les noms de membres d'objet sans guillemets ({a:"hello"}).</span><span class="sxs-lookup"><span data-stu-id="73ada-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="73ada-173"><xref:System.DateTime> temps universel (UTC, Universal Time Coordinated)</span><span class="sxs-lookup"><span data-stu-id="73ada-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="73ada-174">Ne prend pas en charge le format «\\/Date(123456789U)\\/ » ou «\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}])) ?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="73ada-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="73ada-175">Format de prend en charge «\\/Date(123456789U)\\/ » et «\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}])) ?\\) \\ \\/) » en tant que valeurs de date/heure.</span><span class="sxs-lookup"><span data-stu-id="73ada-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="73ada-176">Représentation de dictionnaires</span><span class="sxs-lookup"><span data-stu-id="73ada-176">Representation of dictionaries</span></span>|<span data-ttu-id="73ada-177">Un tableau de KeyValuePair\<K, V >, gère les types de clés qui ne sont pas des chaînes.</span><span class="sxs-lookup"><span data-stu-id="73ada-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="73ada-178">Comme objets JSON réels - mais gère uniquement des types de clé qui sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="73ada-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="73ada-179">Caractères d'échappement</span><span class="sxs-lookup"><span data-stu-id="73ada-179">Escaped characters</span></span>|<span data-ttu-id="73ada-180">Toujours avec une barre oblique d'échappement (/) ; n'autorise jamais de caractères JSON non valides sans séquence d'échappement, tels que "\n".</span><span class="sxs-lookup"><span data-stu-id="73ada-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="73ada-181">Avec une barre oblique d'échappement (/) pour les valeurs DateTime.</span><span class="sxs-lookup"><span data-stu-id="73ada-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="73ada-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73ada-182">See also</span></span>

- [<span data-ttu-id="73ada-183">Guide pratique pour Utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="73ada-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
