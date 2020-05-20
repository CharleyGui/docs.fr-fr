---
title: Identité
description: Architecture des applications .NET natives Cloud pour Azure | Personnelles
ms.date: 05/13/2020
ms.openlocfilehash: 9fa48977e58e2ca5a5f3e231372a4791640a85fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614017"
---
# <a name="identity"></a>Identité

La plupart des applications logicielles doivent avoir une connaissance de l’utilisateur ou du processus qui les appelle. L’utilisateur ou le processus qui interagit avec une application est appelé principal de sécurité, et le processus d’authentification et d’autorisation de ces principaux est appelé « gestion des identités », ou simplement *identité*. Les applications simples peuvent inclure l’ensemble de leur gestion des identités au sein de l’application, mais cette approche n’est pas adaptée à de nombreuses applications et à de nombreux types de principaux de sécurité. Windows prend en charge l’utilisation de Active Directory pour fournir une authentification et une autorisation centralisées.

<!-- (insert figure showing Windows AD auth model) -->

Bien que cette solution soit efficace au sein des réseaux d’entreprise, elle n’est pas conçue pour une utilisation par des utilisateurs ou des applications qui se trouvent en dehors du domaine Active Directory. Avec la croissance des applications basées sur Internet et la montée d’applications Cloud natives, les modèles de sécurité ont évolué.

Dans le modèle d’identité Cloud natif d’aujourd’hui, l’architecture est supposée être distribuée. Les applications peuvent être déployées n’importe où et peuvent communiquer avec d’autres applications n’importe où. Les clients peuvent communiquer avec ces applications depuis n’importe quel endroit, et en fait, les clients peuvent se composer de n’importe quelle combinaison de plateformes et d’appareils. Les solutions d’identité natives du Cloud tirent parti des normes ouvertes pour obtenir un accès sécurisé aux applications à partir des clients. Ces clients vont des utilisateurs humains sur des PC ou téléphones, à d’autres applications hébergées en ligne, à des boîtiers et des appareils IOT qui exécutent n’importe quelle plate-forme logicielle n’importe où dans le monde.

Les solutions d’identité Cloud Native modernes tirent généralement parti des jetons d’accès émis par un service/serveur de jeton sécurisé (STS) à un principal de sécurité une fois leur identité déterminée. Le jeton d’accès, en général un JSON Web Token (JWT), comprend les *revendications* relatives au principal de sécurité. Ces revendications incluent au minimum l’identité de l’utilisateur, mais peuvent également inclure des revendications supplémentaires qui peuvent être utilisées par les applications pour déterminer le niveau d’accès à accorder au principal.

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

En règle générale, le STS est uniquement responsable de l’authentification du principal. La détermination de leur niveau d’accès aux ressources est laissée à d’autres parties de l’application.

## <a name="references"></a>References

- [Plateforme d’identité Microsoft](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Précédent](azure-monitor.md) 
> [Suivant](authentication-authorization.md)
