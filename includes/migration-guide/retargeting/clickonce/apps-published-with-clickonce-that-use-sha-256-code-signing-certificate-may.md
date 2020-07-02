---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615664"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="ba7cd-101">Les applications publiées avec ClickOnce qui utilisent un certificat de signature de code SHA-256 peuvent échouer sur Windows 2003</span><span class="sxs-lookup"><span data-stu-id="ba7cd-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="ba7cd-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ba7cd-102">Details</span></span>

<span data-ttu-id="ba7cd-103">L'exécutable est signé avec SHA256.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="ba7cd-104">Auparavant, il était signé avec SHA1, que le certificat de signature du code ait été SHA-1 ou SHA-256.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="ba7cd-105">Cela s’applique aux :</span><span class="sxs-lookup"><span data-stu-id="ba7cd-105">This applies to:</span></span>

- <span data-ttu-id="ba7cd-106">Toutes les applications générées avec Visual Studio 2012 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="ba7cd-107">Toutes les applications générées avec Visual Studio 2010 ou antérieur en présence de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="ba7cd-108">En outre, si .NET Framework 4.5 (ou une version ultérieure) est présent, le manifeste ClickOnce est également signé avec SHA-256 pour les certificats SHA-256, quelle que soit la version du .NET Framework sur laquelle il a été compilé.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ba7cd-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ba7cd-109">Suggestion</span></span>

<span data-ttu-id="ba7cd-110">Le changement de signature de l’exécutable ClickOnce affecte uniquement les systèmes Windows Server 2003. Vous devez installer le correctif logiciel KB 938397.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="ba7cd-111">Le changement de signature du manifeste avec l'algorithme SHA-256 même quand une application cible .NET Framework 4.0, ou des versions antérieures, présente une dépendance de runtime sur .NET Framework 4.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ba7cd-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="ba7cd-112">Nom</span><span class="sxs-lookup"><span data-stu-id="ba7cd-112">Name</span></span>    | <span data-ttu-id="ba7cd-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="ba7cd-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ba7cd-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="ba7cd-114">Scope</span></span>   | <span data-ttu-id="ba7cd-115">Edge</span><span class="sxs-lookup"><span data-stu-id="ba7cd-115">Edge</span></span>        |
| <span data-ttu-id="ba7cd-116">Version</span><span class="sxs-lookup"><span data-stu-id="ba7cd-116">Version</span></span> | <span data-ttu-id="ba7cd-117">4,5</span><span class="sxs-lookup"><span data-stu-id="ba7cd-117">4.5</span></span>         |
| <span data-ttu-id="ba7cd-118">Type</span><span class="sxs-lookup"><span data-stu-id="ba7cd-118">Type</span></span>    | <span data-ttu-id="ba7cd-119">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ba7cd-119">Retargeting</span></span> |
