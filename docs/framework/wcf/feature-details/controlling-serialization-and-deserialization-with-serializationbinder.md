---
title: Contrôle de la sérialisation et de la désérialisation avec SerializationBinder
ms.date: 07/14/2020
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: be4068411e2154db53a9616df6cf4d83803954e6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293739"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Contrôle de la sérialisation et de la désérialisation avec SerializationBinder

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> n’est pas sécurisé et ***ne peut pas*** être sécurisé. Pour plus d’informations, consultez le [Guide de sécurité BinaryFormatter](../../../standard/serialization/binaryformatter-security-guide.md).

Au cours de la sérialisation, un formateur transmet les informations requises pour créer une instance d'un objet de type et de version corrects. Ces informations comprennent généralement le nom de type et le nom d'assembly complets de l'objet. Par défaut, la désérialisation utilise ces informations pour créer une instance d'un objet identique. Certains utilisateurs auront peut-être besoin de vérifier quelle classe sérialiser et désérialiser, pour les raisons suivantes : la classe d’origine n’existe pas sur l’ordinateur qui effectue la désérialisation, la classe d’origine a été déplacée entre des assemblys ou une version différente de la classe est requise sur le serveur et le client. Pour plus d’informations, consultez [utilisation du Binder de sérialisation](../samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Ces fonctionnalités sont disponibles uniquement lors de l'utilisation de l'objet <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Utilisation de SerializationBinder  

 <xref:System.Runtime.Serialization.SerializationBinder> est une classe abstraite utilisée pour contrôler les types réels utilisés lors de la sérialisation et de la désérialisation. Pour contrôler les types utilisés pendant la sérialisation et la désérialisation, dérivez une classe à partir de <xref:System.Runtime.Serialization.SerializationBinder> et substituez les méthodes <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> et <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>. La méthode <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> prend un <xref:System.Type> et retourne un assembly et un type de nom. La méthode <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> prend un assembly et un type de nom et retourne un <xref:System.Type>.  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation et désérialisation](serialization-and-deserialization.md)
- [Usage of Serialization Binder](../samples/usage-of-serialization-binder.md)
