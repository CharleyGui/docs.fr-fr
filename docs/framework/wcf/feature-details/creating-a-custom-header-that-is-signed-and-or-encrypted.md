---
title: Création d’un en-tête personnalisé signé et/ou chiffré
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: daa594950c25ea4a5c2012183c47231b4688719e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286719"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Création d’un en-tête personnalisé signé et/ou chiffré

Si vous appelez un service autre que WCF à l'aide d'un client WCF, il est parfois nécessaire d'utiliser des en-têtes SOAP personnalisés. Un bogue de canonisation dans WCF empêche les en-têtes personnalisés qui sont signés et chiffrés de fonctionner avec un service non-WCF. Le problème est causé par la canonisation incorrecte des espaces de noms XML par défaut. Ceci pose problème uniquement si vous appelez des services autres que WCF avec en-têtes personnalisés qui sont signés et/ou chiffrés.  Lorsque le service reçoit le message contenant l'en-tête personnalisé signé et/ou chiffré, il n'est pas en mesure de vérifier la signature. Cette solution de contournement évite le bogue de canonisation, permet l'interopérabilité avec les services autres que WCF, mais n'empêche pas l'interopérabilité avec les services WCF.  
  
## <a name="defining-the-custom-header"></a>Définition de l'en-tête personnalisé  

 Les en-têtes personnalisés sont définis en spécifiant un contrat de message et en marquant les membres à envoyer comme en-têtes avec un attribut  <xref:System.ServiceModel.MessageHeaderAttribute>. Pour contourner le bogue de canonisation, vous devez vous assurer que le sérialiseur XML déclare l'espace de noms de l'en-tête personnalisé avec un préfixe plutôt qu'une déclaration d'espace de noms par défaut. Le code suivant montre comment définir le type de données qui sera utilisé en tant qu'en-tête de message avec la déclaration d'espace de noms appropriée.  
  
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
  
 Ce code déclare un nouveau type appelé `msgHeaderElement` qui sera sérialisé à l'aide du sérialiseur XML. Lorsq'une instance de ce type est sérialisée, elle définit un espace de noms avec un préfixe « h », ce qui permet de contourner le bogue de canonisation.  Le contrat de message définit alors une instance de `msgHeaderElement` et la marque avec l'attribut  <xref:System.ServiceModel.MessageHeaderAttribute>, comme illustré dans l'exemple suivant.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Default Message Contract](../samples/default-message-contract.md)
- [Contrats de message](../samples/message-contracts.md)
- [Utilisation de contrats de message](using-message-contracts.md)
