---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269793"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement

BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe BinaryMessageEncodingBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe BinaryMessageEncodingBindingElement a les propriétés suivantes.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Valeur qui spécifie la taille, en octets, de la mémoire tampon utilisée pour l'encodage.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  
  
## <a name="readerquotas"></a>ReaderQuotas  

 Type de données : XmlDictionaryReaderQuotas  
  
 Type d'accès : Lecture seule  
  
 Quotas des lecteurs.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
