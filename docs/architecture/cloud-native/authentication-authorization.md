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
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="90979-103">Authentification et autorisation dans les applications cloud natives</span><span class="sxs-lookup"><span data-stu-id="90979-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="90979-104">*L’authentification* est le processus de détermination de l’identité d’un directeur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="90979-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="90979-105">*L’autorisation* est l’acte d’accorder une autorisation principale authentifiée pour effectuer une action ou accéder à une ressource.</span><span class="sxs-lookup"><span data-stu-id="90979-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="90979-106">Parfois, l’authentification est raccourcie et l’autorisation `AuthN` est raccourcie à `AuthZ`.</span><span class="sxs-lookup"><span data-stu-id="90979-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="90979-107">Les applications cloud-natives doivent s’appuyer sur des protocoles ouverts basés sur HTTP pour authentifier les principaux de sécurité puisque les clients et les applications peuvent fonctionner n’importe où dans le monde sur n’importe quelle plate-forme ou appareil.</span><span class="sxs-lookup"><span data-stu-id="90979-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="90979-108">Le seul facteur commun est HTTP.</span><span class="sxs-lookup"><span data-stu-id="90979-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="90979-109">De nombreuses organisations comptent encore sur des services d’authentification locaux comme Active Directory Federation Services (ADFS).</span><span class="sxs-lookup"><span data-stu-id="90979-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="90979-110">Bien que cette approche ait traditionnellement bien servi les organisations pour les besoins d’authentification sur place, les applications cloud-native bénéficient de systèmes conçus spécifiquement pour le cloud.</span><span class="sxs-lookup"><span data-stu-id="90979-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="90979-111">Un récent avis du Centre national de cybersécurité (NCSC) du Royaume-Uni en 2019 indique que « les organisations qui utilisent Azure AD comme principale source d’authentification diminueront en fait leur risque par rapport à l’ADFS ».</span><span class="sxs-lookup"><span data-stu-id="90979-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="90979-112">Voici quelques raisons énoncées dans [la présente analyse](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) :</span><span class="sxs-lookup"><span data-stu-id="90979-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="90979-113">Accès à l’ensemble complet des technologies de protection des informations d’identification Microsoft.</span><span class="sxs-lookup"><span data-stu-id="90979-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="90979-114">La plupart des organisations comptent déjà sur Azure AD dans une certaine mesure.</span><span class="sxs-lookup"><span data-stu-id="90979-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="90979-115">Le double hachage des hachages NTLM garantit que le compromis ne permettra pas les informations d’identification qui fonctionnent dans l’annuaire actif local.</span><span class="sxs-lookup"><span data-stu-id="90979-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="90979-116">References</span><span class="sxs-lookup"><span data-stu-id="90979-116">References</span></span>

- [<span data-ttu-id="90979-117">Principes fondamentaux de l’authentification</span><span class="sxs-lookup"><span data-stu-id="90979-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="90979-118">Accès aux jetons et réclamations</span><span class="sxs-lookup"><span data-stu-id="90979-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="90979-119">Il est peut-être temps d’abandonner vos services d’authentification sur place</span><span class="sxs-lookup"><span data-stu-id="90979-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="90979-120">[Suivant précédent](identity.md)
>[Next](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="90979-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
