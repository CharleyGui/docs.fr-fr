---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614551"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="1388c-101">Sommes de contrôle de flux de travail passées de MD5 à SHA1</span><span class="sxs-lookup"><span data-stu-id="1388c-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="1388c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1388c-102">Details</span></span>

<span data-ttu-id="1388c-103">Pour prendre en charge le débogage avec Visual Studio, l’exécution du flux de travail génère une somme de contrôle pour une instance de flux de travail à l’aide d’un algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="1388c-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="1388c-104">Dans .NET Framework 4.6.2 et les versions antérieures, le hachage de somme de contrôle de flux de travail utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS.</span><span class="sxs-lookup"><span data-stu-id="1388c-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="1388c-105">À compter de .NET Framework 4.7, l’algorithme est SHA1.</span><span class="sxs-lookup"><span data-stu-id="1388c-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="1388c-106">Si votre code a rendu persistant ces sommes de contrôle, elles seront incompatibles.</span><span class="sxs-lookup"><span data-stu-id="1388c-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1388c-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1388c-107">Suggestion</span></span>

<span data-ttu-id="1388c-108">Si votre code ne peut pas charger des instances de flux de travail en raison d’un échec de la somme de contrôle, essayez de définir le commutateur `AppContext`&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; sur true. Dans le code :</span><span class="sxs-lookup"><span data-stu-id="1388c-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="1388c-109">Ou dans la configuration :</span><span class="sxs-lookup"><span data-stu-id="1388c-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="1388c-110">Nom</span><span class="sxs-lookup"><span data-stu-id="1388c-110">Name</span></span>    | <span data-ttu-id="1388c-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="1388c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1388c-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="1388c-112">Scope</span></span>   | <span data-ttu-id="1388c-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="1388c-113">Minor</span></span>       |
| <span data-ttu-id="1388c-114">Version</span><span class="sxs-lookup"><span data-stu-id="1388c-114">Version</span></span> | <span data-ttu-id="1388c-115">4,7</span><span class="sxs-lookup"><span data-stu-id="1388c-115">4.7</span></span>         |
| <span data-ttu-id="1388c-116">Type</span><span class="sxs-lookup"><span data-stu-id="1388c-116">Type</span></span>    | <span data-ttu-id="1388c-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="1388c-117">Retargeting</span></span> |
