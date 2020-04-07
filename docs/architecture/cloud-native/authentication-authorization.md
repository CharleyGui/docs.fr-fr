---
title: Authentification et autorisation dans les applications cloud-native
description: Architecting Cloud Native .NET Apps for Azure (fr) Authentification et autorisation dans les applications natives Cloud
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805543"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Authentification et autorisation dans les applications cloud natives

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*L’authentification* est le processus de détermination de l’identité d’un directeur de sécurité. *L’autorisation* est l’acte d’accorder une autorisation principale authentifiée pour effectuer une action ou accéder à une ressource. Parfois, l’authentification est raccourcie et l’autorisation `AuthN` est raccourcie à `AuthZ`. Les applications cloud-natives doivent s’appuyer sur des protocoles ouverts basés sur HTTP pour authentifier les principaux de sécurité puisque les clients et les applications peuvent fonctionner n’importe où dans le monde sur n’importe quelle plate-forme ou appareil. Le seul facteur commun est HTTP.

De nombreuses organisations comptent encore sur des services d’authentification locaux comme Active Directory Federation Services (ADFS). Bien que cette approche ait traditionnellement bien servi les organisations pour les besoins d’authentification sur place, les applications cloud-native bénéficient de systèmes conçus spécifiquement pour le cloud. Un récent avis du Centre national de cybersécurité (NCSC) du Royaume-Uni en 2019 indique que « les organisations qui utilisent Azure AD comme principale source d’authentification diminueront en fait leur risque par rapport à l’ADFS ». Voici quelques raisons énoncées dans [la présente analyse](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) :

- Accès à l’ensemble complet des technologies de protection des informations d’identification Microsoft.
- La plupart des organisations comptent déjà sur Azure AD dans une certaine mesure.
- Le double hachage des hachages NTLM garantit que le compromis ne permettra pas les informations d’identification qui fonctionnent dans l’annuaire actif local.

## <a name="references"></a>References

- [Principes fondamentaux de l’authentification](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Accès aux jetons et réclamations](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Il est peut-être temps d’abandonner vos services d’authentification sur place](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Suivant précédent](identity.md)
>[Next](azure-active-directory.md)
