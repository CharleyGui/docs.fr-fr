---
title: Authentification et autorisation dans les applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | Authentification et autorisation dans les applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: e5254560ac82662e5e3ea6a25997516cd2b478b0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614303"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Authentification et autorisation dans les applications cloud natives

L' *authentification* est le processus qui consiste à déterminer l’identité d’un principal de sécurité. L' *autorisation* consiste à accorder à un principal authentifié l’autorisation d’effectuer une action ou d’accéder à une ressource. Parfois, l’authentification est raccourcie `AuthN` et l’autorisation est raccourcie vers `AuthZ` . Les applications Cloud natives doivent s’appuyer sur des protocoles HTTP ouverts pour authentifier les principaux de sécurité, car les clients et les applications peuvent s’exécuter n’importe où dans le monde sur n’importe quelle plateforme ou n’importe quel appareil. Le seul facteur commun est HTTP.

De nombreuses organisations s’appuient toujours sur des services d’authentification locaux tels que Services ADFS (ADFS). Bien que cette approche ait traditionnellement servi les organisations pour des besoins d’authentification locaux, les applications Cloud natives bénéficient des systèmes conçus spécifiquement pour le Cloud. Un avis récent de la du NCSC (National Cyber Security Centre) du Royaume-Uni 2019 déclare que « les organisations qui utilisent Azure AD comme source d’authentification principale vont en fait diminuer leurs risques par rapport à ADFS ». Voici quelques-unes des raisons décrites dans [cette analyse](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) :

- Accès à un ensemble complet de technologies de protection des informations d’identification Microsoft.
- La plupart des organisations utilisent déjà Azure AD dans une certaine mesure.
- Le hachage double des hachages NTLM garantit que la compromission n’autorise pas les informations d’identification qui fonctionnent dans les Active Directory locales.

## <a name="references"></a>References

- [Principes fondamentaux de l’authentification](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Jetons d’accès et revendications](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Il peut être temps d’abandonner vos services d’authentification locaux](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Précédent](identity.md) 
> [Suivant](azure-active-directory.md)
