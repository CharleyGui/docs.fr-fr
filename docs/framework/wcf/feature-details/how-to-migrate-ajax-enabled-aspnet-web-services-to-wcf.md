---
title: 'Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6f356f47922945218e02271371d9ddea36ecc5a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597005"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="0529e-102">Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="0529e-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="0529e-103">Cette rubrique décrit les procédures de migration d’un service ASP.NET AJAX de base vers un service WCF (Windows Communication Foundation compatible AJAX) équivalent.</span><span class="sxs-lookup"><span data-stu-id="0529e-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0529e-104">Il montre comment créer une version WCF équivalente d’un service ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="0529e-105">Les deux services peuvent ensuite être utilisés côte à côte, ou le service WCF peut être utilisé pour remplacer le service ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="0529e-106">La migration d’un service ASP.NET AJAX existant vers un service WCF AJAX vous offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="0529e-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="0529e-107">Vous pouvez exposer votre service AJAX en tant que service SOAP avec une configuration supplémentaire minimale.</span><span class="sxs-lookup"><span data-stu-id="0529e-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="0529e-108">Vous pouvez tirer parti des fonctionnalités WCF, telles que le suivi, etc.</span><span class="sxs-lookup"><span data-stu-id="0529e-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="0529e-109">Les procédures suivantes supposent que vous utilisez Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0529e-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="0529e-110">Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple qui suit les procédures.</span><span class="sxs-lookup"><span data-stu-id="0529e-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="0529e-111">Pour plus d’informations sur l’exposition d’un service WCF via un point de terminaison compatible AJAX, consultez la rubrique [Comment : utiliser la configuration pour ajouter un point de terminaison ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="0529e-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="0529e-112">Pour créer et tester l'application de service Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0529e-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="0529e-113">Ouvrez Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0529e-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="0529e-114">Dans le menu **fichier** , sélectionnez **nouveau**, **projet**, puis **Web**, puis sélectionnez application de **service Web ASP.net**.</span><span class="sxs-lookup"><span data-stu-id="0529e-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="0529e-115">Nommez le projet `ASPHello` et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0529e-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="0529e-116">Supprimez les marques de commentaire dans la ligne du fichier Service1.asmx.cs qui contient `System.Web.Script.Services.ScriptService]` pour rendre ce service compatible avec AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="0529e-117">Dans le menu **générer** , sélectionnez **générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="0529e-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="0529e-118">Dans le menu **Déboguer**, sélectionnez **Exécuter sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="0529e-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="0529e-119">Sur la page web générée, sélectionnez l’opération `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="0529e-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="0529e-120">Cliquez sur le bouton **appeler** sur la `HelloWorld` page de test.</span><span class="sxs-lookup"><span data-stu-id="0529e-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="0529e-121">Vous recevez alors la réponse XML suivante.</span><span class="sxs-lookup"><span data-stu-id="0529e-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="0529e-122">Cette réponse confirme que vous bénéficiez désormais d'un service ASP.NET AJAX fonctionnel et, plus précisément, que le service a exposé un point de terminaison à Service1.asmx/HelloWorld qui répond aux requêtes HTTP POST et retourne du code XML.</span><span class="sxs-lookup"><span data-stu-id="0529e-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="0529e-123">Vous êtes maintenant prêt à convertir ce service pour utiliser un service WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="0529e-124">Pour créer une application de service AJAX WCF équivalente</span><span class="sxs-lookup"><span data-stu-id="0529e-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="0529e-125">Cliquez avec le bouton droit sur le projet **ASPHello** et sélectionnez **Ajouter**, puis **nouvel élément**et **service WCF compatible Ajax**.</span><span class="sxs-lookup"><span data-stu-id="0529e-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="0529e-126">Nommez le service `WCFHello` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0529e-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="0529e-127">Ouvrez le fichier WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="0529e-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="0529e-128">À partir de Service1.asmx.cs, copiez l’implémentation suivante de l' `HelloWorld` opération.</span><span class="sxs-lookup"><span data-stu-id="0529e-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="0529e-129">Collez l’implémentation copiée de l' `HelloWorld` opération dans le fichier WCFHello.svc.cs à la place du code suivant.</span><span class="sxs-lookup"><span data-stu-id="0529e-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="0529e-130">Spécifiez l' `Namespace` attribut pour <xref:System.ServiceModel.ServiceContractAttribute> As `WCFHello` .</span><span class="sxs-lookup"><span data-stu-id="0529e-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="0529e-131">Ajoutez le <xref:System.ServiceModel.Web.WebInvokeAttribute> à l' `HelloWorld` opération et affectez <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> à la propriété la valeur Return <xref:System.ServiceModel.Web.WebMessageFormat.Xml> .</span><span class="sxs-lookup"><span data-stu-id="0529e-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="0529e-132">Notez que si la propriété n'est pas définie, le type de retour par défaut est <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="0529e-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="0529e-133">Dans le menu **générer** , sélectionnez **générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="0529e-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="0529e-134">Ouvrez le fichier WCFHello. svc et, dans le menu **Déboguer** , sélectionnez **exécuter sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="0529e-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="0529e-135">Le service expose maintenant un point de terminaison à `WCFHello.svc/HelloWorld` , qui répond aux requêtes HTTP http.</span><span class="sxs-lookup"><span data-stu-id="0529e-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="0529e-136">Les requêtes HTTP POST ne peuvent pas être testées à partir du navigateur, mais le point de terminaison retourne le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="0529e-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="0529e-137">Les `WCFHello.svc/HelloWorld` points de `Service1.aspx/HelloWorld` terminaison et sont maintenant équivalents d’un point de fonction.</span><span class="sxs-lookup"><span data-stu-id="0529e-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="0529e-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="0529e-138">Example</span></span>
 <span data-ttu-id="0529e-139">Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0529e-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="0529e-140">Le type <xref:System.Xml.XmlDocument> n'est pas pris en charge par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> car il n'est pas sérialisable par <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0529e-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0529e-141">Vous pouvez utiliser un type <xref:System.Xml.Linq.XDocument> ou sérialiser <xref:System.Xml.XmlDocument.DocumentElement%2A> à la place.</span><span class="sxs-lookup"><span data-stu-id="0529e-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="0529e-142">Si les services Web ASMX sont mis à niveau et migrés côte à côte vers les services WCF, évitez de mapper deux types avec le même nom sur le client.</span><span class="sxs-lookup"><span data-stu-id="0529e-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="0529e-143">Cela provoque une exception dans les sérialiseurs si le même type est utilisé dans un <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.ServiceModel.ServiceContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="0529e-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="0529e-144">Si le service WCF est ajouté en premier, l’appel de la méthode sur le service Web ASMX provoque une exception dans <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> parce que la définition de style WCF de l’ordre dans le proxy est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="0529e-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="0529e-145">Si le service Web ASMX est ajouté en premier, l’appel de la méthode sur le service WCF provoque une exception dans <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> parce que la définition de style de service Web de la commande dans le proxy est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="0529e-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="0529e-146">Il existe des différences de comportement importantes entre le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et le <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="0529e-147">Par exemple, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> représente un dictionnaire sous la forme d'un tableau de paires clé/valeur, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX représente un dictionnaire sous la forme d'objets JSON réels.</span><span class="sxs-lookup"><span data-stu-id="0529e-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="0529e-148">Par conséquent, le code suivant est le dictionnaire représenté dans ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0529e-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="0529e-149">Ce dictionnaire est représenté dans des objets JSON comme indiqué dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="0529e-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="0529e-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="0529e-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="0529e-151">{"un" : 1, "deux" : 2} par ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="0529e-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="0529e-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est plus puissant car il peut gérer des dictionnaires où le type de clé n'est pas une chaîne, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="0529e-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="0529e-153">Cependant, ce dernier est plus compatible avec JSON.</span><span class="sxs-lookup"><span data-stu-id="0529e-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="0529e-154">Les différences principales entre ces sérialiseurs sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="0529e-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="0529e-155">Catégorie de différences</span><span class="sxs-lookup"><span data-stu-id="0529e-155">Category of Differences</span></span>|<span data-ttu-id="0529e-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="0529e-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="0529e-157">JavaScriptSerializer ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="0529e-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="0529e-158">Désérialisation de la mémoire tampon vide (nouvel octet [0]) dans <xref:System.Object> (ou <xref:System.Uri> ou d'autres classes).</span><span class="sxs-lookup"><span data-stu-id="0529e-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="0529e-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="0529e-159">SerializationException</span></span>|<span data-ttu-id="0529e-160">null</span><span class="sxs-lookup"><span data-stu-id="0529e-160">null</span></span>|
|<span data-ttu-id="0529e-161">Sérialisation de <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="0529e-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="0529e-162">{}(ou {« __type » : « #System »})</span><span class="sxs-lookup"><span data-stu-id="0529e-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="0529e-163">Null</span><span class="sxs-lookup"><span data-stu-id="0529e-163">Null</span></span>|
|<span data-ttu-id="0529e-164">Sérialisation des membres privés de types [Sérialisable].</span><span class="sxs-lookup"><span data-stu-id="0529e-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="0529e-165">sérialisée</span><span class="sxs-lookup"><span data-stu-id="0529e-165">serialized</span></span>|<span data-ttu-id="0529e-166">n'est pas sérialisé</span><span class="sxs-lookup"><span data-stu-id="0529e-166">not serialized</span></span>|
|<span data-ttu-id="0529e-167">Sérialisation des propriétés publiques de types <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="0529e-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="0529e-168">n'est pas sérialisé</span><span class="sxs-lookup"><span data-stu-id="0529e-168">not serialized</span></span>|<span data-ttu-id="0529e-169">sérialisée</span><span class="sxs-lookup"><span data-stu-id="0529e-169">serialized</span></span>|
|<span data-ttu-id="0529e-170">« Extensions » de JSON</span><span class="sxs-lookup"><span data-stu-id="0529e-170">"Extensions" of JSON</span></span>|<span data-ttu-id="0529e-171">Respecte la spécification JSON, qui exige des guillemets sur les noms de membres d'objet ({"a":"hello"}).</span><span class="sxs-lookup"><span data-stu-id="0529e-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="0529e-172">Prend en charge les noms de membres d'objet sans guillemets ({a:"hello"}).</span><span class="sxs-lookup"><span data-stu-id="0529e-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="0529e-173"><xref:System.DateTime> temps universel (UTC, Universal Time Coordinated)</span><span class="sxs-lookup"><span data-stu-id="0529e-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="0529e-174">Ne prend pas en charge le format « \\ /Date (123456789U) \\ / » ou « \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) ? \\ ) \\ \\ /)".</span><span class="sxs-lookup"><span data-stu-id="0529e-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="0529e-175">Prend en charge le format « \\ /Date (123456789U) \\ / » et « \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) ? \\ ) \\ \\ /)» en tant que valeurs DateTime.</span><span class="sxs-lookup"><span data-stu-id="0529e-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="0529e-176">Représentation de dictionnaires</span><span class="sxs-lookup"><span data-stu-id="0529e-176">Representation of dictionaries</span></span>|<span data-ttu-id="0529e-177">Tableau de KeyValuePair \<K,V> qui gère les types de clé qui ne sont pas des chaînes.</span><span class="sxs-lookup"><span data-stu-id="0529e-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="0529e-178">Comme objets JSON réels - mais gère uniquement des types de clé qui sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="0529e-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="0529e-179">Caractères d'échappement</span><span class="sxs-lookup"><span data-stu-id="0529e-179">Escaped characters</span></span>|<span data-ttu-id="0529e-180">Toujours avec une barre oblique d'échappement (/) ; n'autorise jamais de caractères JSON non valides sans séquence d'échappement, tels que "\n".</span><span class="sxs-lookup"><span data-stu-id="0529e-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="0529e-181">Avec une barre oblique d'échappement (/) pour les valeurs DateTime.</span><span class="sxs-lookup"><span data-stu-id="0529e-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0529e-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0529e-182">See also</span></span>

- [<span data-ttu-id="0529e-183">Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0529e-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
