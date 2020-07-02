---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616050"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="2d47a-101">VB.NET ne prend plus en charge la qualification partielle des espaces de noms pour les API System.Windows</span><span class="sxs-lookup"><span data-stu-id="2d47a-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="2d47a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2d47a-102">Details</span></span>

<span data-ttu-id="2d47a-103">À compter de .NET Framework 4.5.2, les projets VB.NET ne peuvent plus spécifier d’API System.Windows avec des espaces de noms partiellement qualifiés.</span><span class="sxs-lookup"><span data-stu-id="2d47a-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="2d47a-104">Par exemple, la référence à `Windows.Forms.DialogResult` échoue.</span><span class="sxs-lookup"><span data-stu-id="2d47a-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="2d47a-105">Le code doit référencer le nom qualifié complet (<xref:System.Windows.Forms.DialogResult>) ou importer l’espace de noms et référencer <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2d47a-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2d47a-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2d47a-106">Suggestion</span></span>

<span data-ttu-id="2d47a-107">Le code doit être mis à jour pour référencer les API `System.Windows` avec des noms simples (en important l’espace de noms nécessaire) ou avec des noms qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="2d47a-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="2d47a-108">Nom</span><span class="sxs-lookup"><span data-stu-id="2d47a-108">Name</span></span>    | <span data-ttu-id="2d47a-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="2d47a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2d47a-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="2d47a-110">Scope</span></span>   | <span data-ttu-id="2d47a-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="2d47a-111">Minor</span></span>       |
| <span data-ttu-id="2d47a-112">Version</span><span class="sxs-lookup"><span data-stu-id="2d47a-112">Version</span></span> | <span data-ttu-id="2d47a-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="2d47a-113">4.5.2</span></span>       |
| <span data-ttu-id="2d47a-114">Type</span><span class="sxs-lookup"><span data-stu-id="2d47a-114">Type</span></span>    | <span data-ttu-id="2d47a-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2d47a-115">Retargeting</span></span> |
