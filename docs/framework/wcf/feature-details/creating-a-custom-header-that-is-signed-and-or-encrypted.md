---
title: Création d’un en-tête personnalisé signé et/ou chiffré
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0adb4100bca1add2c23ff2c802ddb5e2cb1c368c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579656"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="7689f-102">Création d’un en-tête personnalisé signé et/ou chiffré</span><span class="sxs-lookup"><span data-stu-id="7689f-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="7689f-103">Si vous appelez un service autre que WCF à l'aide d'un client WCF, il est parfois nécessaire d'utiliser des en-têtes SOAP personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7689f-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="7689f-104">Un bogue de canonisation dans WCF empêche les en-têtes personnalisés qui sont signés et chiffrés de fonctionner avec un service non-WCF.</span><span class="sxs-lookup"><span data-stu-id="7689f-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="7689f-105">Le problème est causé par la canonisation incorrecte des espaces de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="7689f-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="7689f-106">Ceci pose problème uniquement si vous appelez des services autres que WCF avec en-têtes personnalisés qui sont signés et/ou chiffrés.</span><span class="sxs-lookup"><span data-stu-id="7689f-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="7689f-107">Lorsque le service reçoit le message contenant l'en-tête personnalisé signé et/ou chiffré, il n'est pas en mesure de vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="7689f-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="7689f-108">Cette solution de contournement évite le bogue de canonisation, permet l'interopérabilité avec les services autres que WCF, mais n'empêche pas l'interopérabilité avec les services WCF.</span><span class="sxs-lookup"><span data-stu-id="7689f-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="7689f-109">Définition de l'en-tête personnalisé</span><span class="sxs-lookup"><span data-stu-id="7689f-109">Defining the custom header</span></span>  
 <span data-ttu-id="7689f-110">Les en-têtes personnalisés sont définis en spécifiant un contrat de message et en marquant les membres à envoyer comme en-têtes avec un attribut  <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7689f-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="7689f-111">Pour contourner le bogue de canonisation, vous devez vous assurer que le sérialiseur XML déclare l'espace de noms de l'en-tête personnalisé avec un préfixe plutôt qu'une déclaration d'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7689f-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="7689f-112">Le code suivant montre comment définir le type de données qui sera utilisé en tant qu'en-tête de message avec la déclaration d'espace de noms appropriée.</span><span class="sxs-lookup"><span data-stu-id="7689f-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```csharp
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7689f-113">Ce code déclare un nouveau type appelé `msgHeaderElement` qui sera sérialisé à l'aide du sérialiseur XML.</span><span class="sxs-lookup"><span data-stu-id="7689f-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="7689f-114">Lorsq'une instance de ce type est sérialisée, elle définit un espace de noms avec un préfixe « h », ce qui permet de contourner le bogue de canonisation.</span><span class="sxs-lookup"><span data-stu-id="7689f-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="7689f-115">Le contrat de message définit alors une instance de `msgHeaderElement` et la marque avec l'attribut  <xref:System.ServiceModel.MessageHeaderAttribute>, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7689f-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7689f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7689f-116">See also</span></span>

- [<span data-ttu-id="7689f-117">Default Message Contract</span><span class="sxs-lookup"><span data-stu-id="7689f-117">Default Message Contract</span></span>](../samples/default-message-contract.md)
- [<span data-ttu-id="7689f-118">Contrats de message</span><span class="sxs-lookup"><span data-stu-id="7689f-118">Message Contracts</span></span>](../samples/message-contracts.md)
- [<span data-ttu-id="7689f-119">Utilisation de contrats de message</span><span class="sxs-lookup"><span data-stu-id="7689f-119">Using Message Contracts</span></span>](using-message-contracts.md)
