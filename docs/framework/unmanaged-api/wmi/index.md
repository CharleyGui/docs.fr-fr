---
title: WMI et compteurs de performances (référence des API non managées)
description: Fournit une synthèse de l’API .NET Framework non managée pour les informations de compteurs de performance et WMI.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127418"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>WMI (Windows Management Instrumentation) et compteurs de performances (référence des API non managées)

L’API non managée .NET Framework WMI et compteurs de performances se compose d’un ensemble de fonctions qui wrappent les appels à l’[API Windows Management Instrumentation native](/windows/desktop/WmiSdk/com-api-for-wmi). Elle vous permet de développer des outils et des bibliothèques qui gèrent et analysent des systèmes informatiques distants.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

L’API comprend les fonctions suivantes :

| Fonction | Description |
|---------|---------|
| [BeginEnumeration, fonction](beginenumeration.md) | Réinitialise l’énumérateur au début d’une énumération de propriétés d’objet WMI. |
| [BeginMethodEnumeration, fonction](beginmethodenumeration.md) |  Commence une énumération des méthodes disponibles pour un objet. |
| [BlessIWbemServices, fonction](blessiwbemservices.md) | Indique si les informations d’identification de l’utilisateur autorisent l’accès à une classe IWbemServices spécifiée. |
| [BlessIWbemServicesObject, fonction](blessiwbemservicesobject.md) | Indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet de service IWbem spécifié. |
| [Clone, fonction](clone.md) | Retourne un nouvel objet qui est un clone complet de l’objet actuel. |
| [CloneEnumWbemClassObject, fonction](cloneenumwbemclassobject.md) | Effectue une copie logique d’un énumérateur, en conservant sa position actuelle dans une énumération. |
| [CompareTo, fonction](compareto.md) | Compare un objet à un autre objet WMI. |
| [ConnectServerWmi, fonction](connectserverwmi.md) | Crée une connexion via DCOM à un espace de noms WMI sur un ordinateur spécifié. |
| [CreateClassEnumWmi, fonction](createclassenumwmi.md) | Retourne un énumérateur pour toutes les classes qui remplissent les critères de sélection spécifiés. |
| [CreateInstanceEnumWmi, fonction](createinstanceenumwmi.md) | Retourne un énumérateur qui retourne les instances d’une classe spécifiée remplissant les critères de sélection spécifiés. |
| [Supprimer la fonction](delete.md) | Supprime une propriété spécifiée d’une définition de classe et tous ses qualificateurs. |
| [DeleteMethod, fonction](deletemethod.md) | Supprime une méthode spécifiée d’une définition de classe CIM. |
| [EndEnumeration, fonction](endenumeration.md) | Met fin à une séquence d’énumération. |
| [EndMethodEnumeration, fonction](endmethodenumeration.md) | Met fin à une séquence d’énumération lancée en appelant la [fonction BeginMethodEnumeration](beginmethodenumeration.md). |
| [ExecNotificationQueryWmi, fonction](execnotificationquerywmi.md) | Exécute une requête pour recevoir des événements. |
| [ExecQueryWmi, fonction](execquerywmi.md) | Exécute une requête pour récupérer des objets. |
| [FormatFromRawValue, fonction](formatfromrawvalue.md) | Convertit une valeur de données de performances brute au format spécifié, ou deux valeurs de données de performances brutes si la conversion de format est basé sur l’heure. |
| [Get, fonction](get.md) | Récupère une valeur de propriété spécifiée si elle existe. |
| [GetCurrentApartmentType, fonction](getcurrentapartmenttype.md) | Récupère le type de cloisonnement dans lequel l’appelant s’exécute. |
| [GetDemultiplexedStub, fonction](getdemultiplexedstub.md) | Crée un récepteur de redirecteur d’objet pour aider un client lors de la réception des appels asynchrones WMI. |
| [GetErrorInfo, fonction](geterrorinfo.md) | Récupère les informations d’erreur à partir de l’appel de fonction précédent. |
| [GetMethod, fonction](getmethod.md) | Récupère les informations sur la méthode spécifiée. |
| [GetMethodOrigin, fonction](getmethodorigin.md) | Détermine la classe dans laquelle une méthode est déclarée. |
| [GetMethodQualifierSet, fonction](getmethodqualifierset.md) | Récupère le jeu de qualificateurs pour une méthode particulière. |
| [GetNames, fonction](getnames.md) | Récupère une partie ou l’ensemble des noms des propriétés d’un objet. |
| [GetObjectText, fonction](getobjecttext.md) | Retourne un rendu textuel d’un objet dans la syntaxe MOF. |
| [GetPropertyHandle, fonction](getpropertyhandle.md) | Retourne un handle unique qui identifie une propriété. |
| [GetPropertyOrigin, fonction](getpropertyorigin.md) | Détermine la classe dans laquelle une propriété est déclarée. |
| [GetPropertyQualifierSet, fonction](getpropertyqualifierset.md) | Récupère le jeu de qualificateurs pour une propriété particulière.  |
| [GetQualifierSet, fonction](getqualifierset.md) | Récupère le jeu de qualificateurs pour une instance de classe ou une définition de classe. |
| [InheritsFrom, fonction](inheritsfrom.md) | Détermine si l’instance ou la classe active dérive d’une classe parente spécifié. |
| [Initialize, fonction](initialize.md) | Effectue l’initialisation WMI. |
| [Next, fonction](next.md) | Récupère la propriété suivante dans une énumération. |
| [NextMethod, fonction](nextmethod.md) | Récupère la méthode suivante dans une énumération. |
| [Fonction Put](put.md) | Affecte une nouvelle valeur à une propriété nommée. |
| [PutClassWmi, fonction](putclasswmi.md) | Crée une classe ou met à jour une classe existante. |
| [PutInstanceWmi, fonction](putinstancewmi.md) | Crée ou met à jour une instance d’une classe existante. L’instance est écrite dans le référentiel WMI. |
| [PutMethod, fonction](putmethod.md) | Crée une méthode. |
| [QualifierSet_BeginEnumeration, fonction](qualifierset-beginenumeration.md) | Réinitialise un énumérateur des qualificateurs d’un objet au début de l’énumération. |
| [QualifierSet_Delete, fonction](qualifierset-delete.md) | Supprime un qualificateur spécifié par nom.  |
| [QualifierSet_EndEnumeration, fonction](qualifierset-endenumeration.md) | Met fin à l’énumération commencée avec un appel à la fonction `QualifierSet_BeginEnumeration`. |
| [QualifierSet_Get, fonction](qualifierset-get.md) | Obtient le qualificateur nommé spécifié.  |
| [QualifierSet_GetNames, fonction](qualifierset-getnames.md) | Récupère les noms de tous les qualificateurs ou des qualificateurs spécifiés qui sont disponibles à partir de la propriété ou de l’objet actif. |
| [QualifierSet_Next, fonction](qualifierset-next.md) | Récupère le qualificateur suivant dans une énumération commencée avec un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
| [QualifierSet_Put, fonction](qualifierset-put.md) | Écrit la valeur et le qualificateur nommés. |
| [ResetSecurity, fonction](resetsecurity.md) | Assigne le jeton d’emprunt d’identité fourni au thread actif. |
| [SetSecurity, fonction](setsecurity.md) | Récupère le jeton d’emprunt d’identité associé au thread actif. |
| [SpawnDerivedClass, fonction](spawnderivedclass.md) | Crée un objet de classe dérivé à partir d’un objet spécifié. |
| [SpawnInstance, fonction](spawninstance.md) | Crée une instance d’une classe. |
| [VerifyClient, fonction](verifyclientkey.md) | Garantit que la clé du client offre une sécurité correcte. |
| [WritePropertyValue, fonction](writepropertyvalue.md) | Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété. |

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées](../index.md)
