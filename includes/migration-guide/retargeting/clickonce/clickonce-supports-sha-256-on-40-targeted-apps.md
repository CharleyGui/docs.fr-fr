---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615652"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="e6cc0-101">ClickOnce prend en charge SHA-256 sur les applications ciblées par la version 4.0</span><span class="sxs-lookup"><span data-stu-id="e6cc0-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="e6cc0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e6cc0-102">Details</span></span>

<span data-ttu-id="e6cc0-103">Avant, une application ClickOnce disposant d’un certificat signé avec SHA-256 nécessitait la présence de .NET Framework 4.5 ou ultérieur, même si l’application ciblait la version 4.0.</span><span class="sxs-lookup"><span data-stu-id="e6cc0-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="e6cc0-104">Désormais, les applications ClickOnce ciblées par .NET Framework 4.0 peuvent s’exécuter sur .NET Framework 4.0, même si elles sont signées avec SHA-256.</span><span class="sxs-lookup"><span data-stu-id="e6cc0-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e6cc0-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e6cc0-105">Suggestion</span></span>

<span data-ttu-id="e6cc0-106">Ce changement supprime cette dépendance et permet aux certificats SHA-256 d’être utilisés pour signer des applications ClickOnce qui ciblent .NET Framework 4 et les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="e6cc0-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="e6cc0-107">Nom</span><span class="sxs-lookup"><span data-stu-id="e6cc0-107">Name</span></span>    | <span data-ttu-id="e6cc0-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e6cc0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e6cc0-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e6cc0-109">Scope</span></span>   | <span data-ttu-id="e6cc0-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="e6cc0-110">Minor</span></span>       |
| <span data-ttu-id="e6cc0-111">Version</span><span class="sxs-lookup"><span data-stu-id="e6cc0-111">Version</span></span> | <span data-ttu-id="e6cc0-112">4.6</span><span class="sxs-lookup"><span data-stu-id="e6cc0-112">4.6</span></span>         |
| <span data-ttu-id="e6cc0-113">Type</span><span class="sxs-lookup"><span data-stu-id="e6cc0-113">Type</span></span>    | <span data-ttu-id="e6cc0-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="e6cc0-114">Retargeting</span></span> |
