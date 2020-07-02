---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616246"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="e0c4b-101">Les sommes de contrôle XAML de workflow pour les symboles passent de SHA1 à SHA256</span><span class="sxs-lookup"><span data-stu-id="e0c4b-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="e0c4b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e0c4b-102">Details</span></span>

<span data-ttu-id="e0c4b-103">Pour prendre en charge le débogage avec Visual Studio, l’exécution du workflow génère une somme de contrôle pour un fichier XAML de workflow à l’aide d’un algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="e0c4b-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="e0c4b-104">Dans .NET Framework 4.6.2 et les versions antérieures, le hachage de somme de contrôle de flux de travail utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS.</span><span class="sxs-lookup"><span data-stu-id="e0c4b-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="e0c4b-105">À compter de .NET Framework 4.7, l’algorithme par défaut est passé à SHA1.</span><span class="sxs-lookup"><span data-stu-id="e0c4b-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="e0c4b-106">À compter de .NET Framework 4.8, l’algorithme par défaut est passé à SHA256.</span><span class="sxs-lookup"><span data-stu-id="e0c4b-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e0c4b-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e0c4b-107">Suggestion</span></span>

<span data-ttu-id="e0c4b-108">Si votre code n’est pas en mesure de charger des instances de workflow ou de rechercher les symboles appropriés en raison d’une erreur de somme de contrôle, essayez de définir le `AppContext` commutateur «Switch.SysTEM. Activities. UseSHA1HashForDebuggerSymbols» en `true` .</span><span class="sxs-lookup"><span data-stu-id="e0c4b-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="e0c4b-109">Dans le code :</span><span class="sxs-lookup"><span data-stu-id="e0c4b-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="e0c4b-110">Ou dans la configuration :</span><span class="sxs-lookup"><span data-stu-id="e0c4b-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="e0c4b-111">Nom</span><span class="sxs-lookup"><span data-stu-id="e0c4b-111">Name</span></span>    | <span data-ttu-id="e0c4b-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="e0c4b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e0c4b-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="e0c4b-113">Scope</span></span>   | <span data-ttu-id="e0c4b-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="e0c4b-114">Minor</span></span>       |
| <span data-ttu-id="e0c4b-115">Version</span><span class="sxs-lookup"><span data-stu-id="e0c4b-115">Version</span></span> | <span data-ttu-id="e0c4b-116">4.8</span><span class="sxs-lookup"><span data-stu-id="e0c4b-116">4.8</span></span>         |
| <span data-ttu-id="e0c4b-117">Type</span><span class="sxs-lookup"><span data-stu-id="e0c4b-117">Type</span></span>    | <span data-ttu-id="e0c4b-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="e0c4b-118">Retargeting</span></span> |
