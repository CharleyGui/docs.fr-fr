---
title: Authentification et autorisation dans les applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | Authentification et autorisation dans les applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: bbd2df110dd7a7dc7363e9c07d87f1fa12f4e464
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161137"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Authentification et autorisation dans les applications cloud natives

L' *authentification* est le processus qui consiste à déterminer l’identité d’un principal de sécurité. L' *autorisation* consiste à accorder à un principal authentifié l’autorisation d’effectuer une action ou d’accéder à une ressource. Parfois, l’authentification est raccourcie `AuthN` et l’autorisation est raccourcie vers `AuthZ` . Les applications Cloud natives doivent s’appuyer sur des protocoles HTTP ouverts pour authentifier les principaux de sécurité, car les clients et les applications peuvent s’exécuter n’importe où dans le monde sur n’importe quelle plateforme ou n’importe quel appareil. Le seul facteur commun est HTTP.

De nombreuses organisations s’appuient toujours sur des services d’authentification locaux tels que Services ADFS (ADFS). Bien que cette approche ait traditionnellement servi les organisations pour des besoins d’authentification locaux, les applications Cloud natives bénéficient des systèmes conçus spécifiquement pour le Cloud. Un avis récent de la du NCSC (National Cyber Security Centre) du Royaume-Uni 2019 déclare que « les organisations qui utilisent Azure AD comme source d’authentification principale vont en fait diminuer leurs risques par rapport à ADFS ». Voici quelques-unes des raisons décrites dans [cette analyse](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) :

- Accès à un ensemble complet de technologies de protection des informations d’identification Microsoft.
- La plupart des organisations utilisent déjà Azure AD dans une certaine mesure.
- Le hachage double des hachages NTLM garantit que la compromission n’autorise pas les informations d’identification qui fonctionnent dans les Active Directory locales.

## <a name="references"></a>Références

- [Principes fondamentaux de l’authentification](/azure/active-directory/develop/authentication-scenarios)
- [Jetons d’accès et revendications](/azure/active-directory/develop/access-tokens)
- [Il peut être temps d’abandonner vos services d’authentification locaux](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Précédent](identity.md) 
> [Suivant](azure-active-directory.md)
