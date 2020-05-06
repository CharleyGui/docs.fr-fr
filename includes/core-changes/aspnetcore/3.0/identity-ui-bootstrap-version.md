---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394129"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="d49ef-101">Identité : la version d’amorçage par défaut de l’interface utilisateur a changé</span><span class="sxs-lookup"><span data-stu-id="d49ef-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="d49ef-102">À partir de ASP.NET Core 3,0, l’interface utilisateur d’identité utilise la version 4 de bootstrap par défaut.</span><span class="sxs-lookup"><span data-stu-id="d49ef-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d49ef-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d49ef-103">Version introduced</span></span>

<span data-ttu-id="d49ef-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d49ef-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d49ef-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d49ef-105">Old behavior</span></span>

<span data-ttu-id="d49ef-106">L' `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` appel de méthode était le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="d49ef-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d49ef-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d49ef-107">New behavior</span></span>

<span data-ttu-id="d49ef-108">L' `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` appel de la méthode est le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="d49ef-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d49ef-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d49ef-109">Reason for change</span></span>

<span data-ttu-id="d49ef-110">Le bootstrap 4 a été publié au cours de la période de ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d49ef-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d49ef-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d49ef-111">Recommended action</span></span>

<span data-ttu-id="d49ef-112">Vous êtes affecté par cette modification si vous utilisez l’interface utilisateur d' `Startup.ConfigureServices` identité par défaut et que vous l’avez ajoutée comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d49ef-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="d49ef-113">Effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d49ef-113">Take one of the following actions:</span></span>

- <span data-ttu-id="d49ef-114">Migrez votre application pour utiliser bootstrap 4 à l’aide de leur [Guide de migration](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="d49ef-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="d49ef-115">Mise `Startup.ConfigureServices` à jour pour appliquer l’utilisation du bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="d49ef-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="d49ef-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d49ef-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="d49ef-117">Category</span><span class="sxs-lookup"><span data-stu-id="d49ef-117">Category</span></span>

<span data-ttu-id="d49ef-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d49ef-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d49ef-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="d49ef-119">Affected APIs</span></span>

<span data-ttu-id="d49ef-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="d49ef-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
