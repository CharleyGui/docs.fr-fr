---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 6590c5188e4e1758987a75fbd007099703ea6bc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250422"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement

MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe MsmqTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe MsmqTransportBindingElement a les propriétés suivantes :  
  
### <a name="maxpoolsize"></a>MaxPoolSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Taille maximale du pool contenant des objets de message MSMQ internes.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Valeur d'énumération qui indique le transport de canal de communication mis en file d'attente que cette liaison utilise.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Retourne une valeur Boolean qui indique si les adresses de file d'attente doivent être converties à l'aide d'Active Directory.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
