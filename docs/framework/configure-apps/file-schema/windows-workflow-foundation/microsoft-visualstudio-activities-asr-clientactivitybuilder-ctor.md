---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947629"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a>Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
Crée une instance de la classe [Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a>Paramètres  
  
## <a name="parameter-values"></a>Valeurs des paramètres  
 *operationDescription*  
  
 Décrit l'opération à effectuer dans l'activité de workflow qui doit être générée, notamment le nom de l'opération, le type de retour et les informations de paramètre. La valeur de ce paramètre ne doit pas être **null**. Elle doit décrire une opération synchrone qui utilise un contrat de message et prend un argument avec un message. Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
 *configurationName*  
  
 Spécifie le nom de configuration du point de terminaison. La valeur de ce paramètre ne doit pas être **null** ou vide. Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
 *proxyNamespace*  
  
 Spécifie l'espace de noms du service pour l'opération. La valeur de ce paramètre ne doit pas être **null** ou vide. Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
## <a name="see-also"></a>Voir aussi

- [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
