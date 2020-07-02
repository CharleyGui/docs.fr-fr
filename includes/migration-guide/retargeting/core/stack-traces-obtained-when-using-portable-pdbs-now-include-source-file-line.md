---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614533"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="20ab6-101">Les traces obtenues durant l’utilisation de fichiers PDB portables incluent désormais les informations sur les lignes et les fichiers sources, si elles sont demandées</span><span class="sxs-lookup"><span data-stu-id="20ab6-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="20ab6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="20ab6-102">Details</span></span>

<span data-ttu-id="20ab6-103">À compter de .NET Framework 4.7.2, les traces obtenues durant l’utilisation de fichiers PDB portables incluent les informations sur les lignes et les fichiers sources quand elles sont demandées.</span><span class="sxs-lookup"><span data-stu-id="20ab6-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="20ab6-104">Dans les versions antérieures de .NET Framework 4.7.2, les informations sur les lignes et les fichiers sources n’étaient pas disponibles pendant l’utilisation de fichiers PDB portables même si elles étaient explicitement demandées.</span><span class="sxs-lookup"><span data-stu-id="20ab6-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20ab6-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="20ab6-105">Suggestion</span></span>

<span data-ttu-id="20ab6-106">Pour les applications qui ciblent .NET Framework 4.7.2, vous pouvez refuser les informations sur les lignes et les fichiers sources durant l’utilisation de fichiers PDB portables en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="20ab6-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="20ab6-107">Pour les applications qui ciblent des versions antérieures de .NET Framework mais qui s’exécutent sur .NET Framework 4.7.2 ou une version ultérieure, vous pouvez accepter les informations sur les lignes et les fichiers sources durant l’utilisation de fichiers PDB portables en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :</span><span class="sxs-lookup"><span data-stu-id="20ab6-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="20ab6-108">Nom</span><span class="sxs-lookup"><span data-stu-id="20ab6-108">Name</span></span>    | <span data-ttu-id="20ab6-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="20ab6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20ab6-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="20ab6-110">Scope</span></span>   | <span data-ttu-id="20ab6-111">Edge</span><span class="sxs-lookup"><span data-stu-id="20ab6-111">Edge</span></span>        |
| <span data-ttu-id="20ab6-112">Version</span><span class="sxs-lookup"><span data-stu-id="20ab6-112">Version</span></span> | <span data-ttu-id="20ab6-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="20ab6-113">4.7.2</span></span>       |
| <span data-ttu-id="20ab6-114">Type</span><span class="sxs-lookup"><span data-stu-id="20ab6-114">Type</span></span>    | <span data-ttu-id="20ab6-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="20ab6-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="20ab6-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="20ab6-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
