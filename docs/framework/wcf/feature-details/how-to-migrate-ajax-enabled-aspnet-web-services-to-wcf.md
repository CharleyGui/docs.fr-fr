---
title: 'Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 89c9601ba6afcef9733d7653564a98664a1ed70f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241900"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF

Cette rubrique décrit les procédures de migration d’un service ASP.NET AJAX de base vers un service WCF (Windows Communication Foundation compatible AJAX) équivalent. Il montre comment créer une version WCF équivalente d’un service ASP.NET AJAX. Les deux services peuvent ensuite être utilisés côte à côte, ou le service WCF peut être utilisé pour remplacer le service ASP.NET AJAX.

 La migration d’un service ASP.NET AJAX existant vers un service WCF AJAX vous offre les avantages suivants :

- Vous pouvez exposer votre service AJAX en tant que service SOAP avec une configuration supplémentaire minimale.

- Vous pouvez tirer parti des fonctionnalités WCF, telles que le suivi, etc.

 Les procédures suivantes supposent que vous utilisez Visual Studio 2012.

 Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple qui suit les procédures.

 Pour plus d’informations sur l’exposition d’un service WCF via un point de terminaison compatible AJAX, consultez la rubrique [Comment : utiliser la configuration pour ajouter un point de terminaison ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Pour créer et tester l'application de service Web ASP.NET

1. Ouvrez Visual Studio 2012.

2. Dans le menu **fichier** , sélectionnez **nouveau**, **projet**, puis **Web**, puis sélectionnez application de **service Web ASP.net**.

3. Nommez le projet `ASPHello` et cliquez sur **OK**.

4. Supprimez les marques de commentaire dans la ligne du fichier Service1.asmx.cs qui contient `System.Web.Script.Services.ScriptService]` pour rendre ce service compatible avec AJAX.

5. Dans le menu **générer** , sélectionnez **générer la solution**.

6. Dans le menu **Déboguer**, sélectionnez **Démarrer sans débogage**.

7. Sur la page web générée, sélectionnez l’opération `HelloWorld`.

8. Cliquez sur le bouton **appeler** sur la `HelloWorld` page de test. Vous recevez alors la réponse XML suivante.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Cette réponse confirme que vous bénéficiez désormais d'un service ASP.NET AJAX fonctionnel et, plus précisément, que le service a exposé un point de terminaison à Service1.asmx/HelloWorld qui répond aux requêtes HTTP POST et retourne du code XML.

     Vous êtes maintenant prêt à convertir ce service pour utiliser un service WCF AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Pour créer une application de service AJAX WCF équivalente

1. Cliquez avec le bouton droit sur le projet **ASPHello** et sélectionnez **Ajouter**, puis **nouvel élément** et **service WCF compatible Ajax**.

2. Nommez le service `WCFHello` , puis cliquez sur **Ajouter**.

3. Ouvrez le fichier WCFHello.svc.cs.

4. À partir de Service1.asmx.cs, copiez l’implémentation suivante de l' `HelloWorld` opération.

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. Collez l’implémentation copiée de l' `HelloWorld` opération dans le fichier WCFHello.svc.cs à la place du code suivant.

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. Spécifiez l' `Namespace` attribut pour <xref:System.ServiceModel.ServiceContractAttribute> As `WCFHello` .

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Ajoutez le <xref:System.ServiceModel.Web.WebInvokeAttribute> à l' `HelloWorld` opération et affectez <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> à la propriété la valeur Return <xref:System.ServiceModel.Web.WebMessageFormat.Xml> . Notez que si la propriété n'est pas définie, le type de retour par défaut est <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. Dans le menu **générer** , sélectionnez **générer la solution**.

9. Ouvrez le fichier WCFHello. svc et, dans le menu **Déboguer** , sélectionnez **exécuter sans débogage**.

10. Le service expose maintenant un point de terminaison à `WCFHello.svc/HelloWorld` , qui répond aux requêtes HTTP http. Les requêtes HTTP POST ne peuvent pas être testées à partir du navigateur, mais le point de terminaison retourne le code XML suivant.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. Les `WCFHello.svc/HelloWorld` points de `Service1.aspx/HelloWorld` terminaison et sont maintenant équivalents d’un point de fonction.

## <a name="example"></a> Exemple

 Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple suivant.

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

 Le type <xref:System.Xml.XmlDocument> n'est pas pris en charge par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> car il n'est pas sérialisable par <xref:System.Xml.Serialization.XmlSerializer>. Vous pouvez utiliser un type <xref:System.Xml.Linq.XDocument> ou sérialiser <xref:System.Xml.XmlDocument.DocumentElement%2A> à la place.

 Si les services Web ASMX sont mis à niveau et migrés côte à côte vers les services WCF, évitez de mapper deux types avec le même nom sur le client. Cela provoque une exception dans les sérialiseurs si le même type est utilisé dans un <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.ServiceModel.ServiceContractAttribute> :

- Si le service WCF est ajouté en premier, l’appel de la méthode sur le service Web ASMX provoque une exception dans <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> parce que la définition de style WCF de l’ordre dans le proxy est prioritaire.

- Si le service Web ASMX est ajouté en premier, l’appel de la méthode sur le service WCF provoque une exception dans <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> parce que la définition de style de service Web de la commande dans le proxy est prioritaire.

 Il existe des différences de comportement importantes entre le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et le <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX. Par exemple, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> représente un dictionnaire sous la forme d'un tableau de paires clé/valeur, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX représente un dictionnaire sous la forme d'objets JSON réels. Par conséquent, le code suivant est le dictionnaire représenté dans ASP.NET AJAX.

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Ce dictionnaire est représenté dans des objets JSON comme indiqué dans la liste suivante :

- [{"Key":"one","Value":1},{"Key":"two","Value":2}] par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"un" : 1, "deux" : 2} par ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est plus puissant car il peut gérer des dictionnaires où le type de clé n'est pas une chaîne, alors que <xref:System.Web.Script.Serialization.JavaScriptSerializer> ne le peut pas. Cependant, ce dernier est plus compatible avec JSON.

 Les différences principales entre ces sérialiseurs sont résumées dans le tableau suivant.

|Catégorie de différences|DataContractJsonSerializer|JavaScriptSerializer ASP.NET AJAX|
|-----------------------------|--------------------------------|---------------------------------------|
|Désérialisation de la mémoire tampon vide (nouvel octet [0]) dans <xref:System.Object> (ou <xref:System.Uri> ou d'autres classes).|SerializationException|null|
|Sérialisation de <xref:System.DBNull.Value>|{} (ou {« __type » : « #System »})|Null|
|Sérialisation des membres privés de types [Sérialisable].|sérialisée|n'est pas sérialisé|
|Sérialisation des propriétés publiques de types <xref:System.Runtime.Serialization.ISerializable>.|n'est pas sérialisé|sérialisée|
|« Extensions » de JSON|Respecte la spécification JSON, qui exige des guillemets sur les noms de membres d'objet ({"a":"hello"}).|Prend en charge les noms de membres d'objet sans guillemets ({a:"hello"}).|
|<xref:System.DateTime> temps universel (UTC, Universal Time Coordinated)|Ne prend pas en charge le format « \\ /Date (123456789U) \\ / » ou « \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) ? \\ ) \\ \\ /)".|Prend en charge le format « \\ /Date (123456789U) \\ / » et « \\ /date \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ])) ? \\ ) \\ \\ /)» en tant que valeurs DateTime.|
|Représentation de dictionnaires|Tableau de KeyValuePair \<K,V> qui gère les types de clé qui ne sont pas des chaînes.|Comme objets JSON réels - mais gère uniquement des types de clé qui sont des chaînes.|
|Caractères d'échappement|Toujours avec une barre oblique d'échappement (/) ; n'autorise jamais de caractères JSON non valides sans séquence d'échappement, tels que "\n".|Avec une barre oblique d'échappement (/) pour les valeurs DateTime.|

## <a name="see-also"></a>Voir aussi

- [Procédure : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
