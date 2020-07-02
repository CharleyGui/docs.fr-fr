---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614478"
---
### <a name="long-path-support"></a><span data-ttu-id="b71ec-101">Prise en charge des chemins d’accès longs</span><span class="sxs-lookup"><span data-stu-id="b71ec-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="b71ec-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b71ec-102">Details</span></span>

<span data-ttu-id="b71ec-103">À partir des applications qui ciblent .NET Framework 4.6.2, les chemins longs (comprenant jusqu’à 32 000 caractères) sont pris en charge et la limite de 260 caractères (ou `MAX_PATH`) sur la longueur du chemin est supprimée. Pour les applications qui sont recompilées pour cibler .NET Framework 4.6.2, les chemins de code qui levaient précédemment un <xref:System.IO.PathTooLongException?displayProperty=fullName> car un chemin dépassait 260 caractères lèvent désormais un <xref:System.IO.PathTooLongException?displayProperty=fullName> uniquement quand les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="b71ec-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="b71ec-104">La longueur du chemin est supérieure à <xref:System.Int16.MaxValue> (32 767) caractères.</span><span class="sxs-lookup"><span data-stu-id="b71ec-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="b71ec-105">Le système d’exploitation renvoie `COR_E_PATHTOOLONG` ou son équivalent.</span><span class="sxs-lookup"><span data-stu-id="b71ec-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="b71ec-106">Pour les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, le runtime levait automatiquement un <xref:System.IO.PathTooLongException?displayProperty=fullName> chaque fois qu’un chemin comportait plus de 260 caractères.</span><span class="sxs-lookup"><span data-stu-id="b71ec-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b71ec-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b71ec-107">Suggestion</span></span>

<span data-ttu-id="b71ec-108">Pour les applications qui ciblent .NET Framework 4.6.2, vous pouvez refuser la prise en charge des chemins longs en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="b71ec-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="b71ec-109">Pour les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure, vous pouvez accepter la prise en charge des chemins longs en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="b71ec-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="b71ec-110">Nom</span><span class="sxs-lookup"><span data-stu-id="b71ec-110">Name</span></span>    | <span data-ttu-id="b71ec-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="b71ec-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b71ec-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="b71ec-112">Scope</span></span>   | <span data-ttu-id="b71ec-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="b71ec-113">Minor</span></span>       |
| <span data-ttu-id="b71ec-114">Version</span><span class="sxs-lookup"><span data-stu-id="b71ec-114">Version</span></span> | <span data-ttu-id="b71ec-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b71ec-115">4.6.2</span></span>       |
| <span data-ttu-id="b71ec-116">Type</span><span class="sxs-lookup"><span data-stu-id="b71ec-116">Type</span></span>    | <span data-ttu-id="b71ec-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="b71ec-117">Retargeting</span></span> |
