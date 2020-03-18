---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394129"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="a4a0f-101">Identité: Version Bootstrap par défaut de l’interface utilisateur changé</span><span class="sxs-lookup"><span data-stu-id="a4a0f-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="a4a0f-102">À partir de ASP.NET Core 3.0, Identity UI par défaut à l’utilisation de la version 4 de Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="a4a0f-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a4a0f-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a4a0f-103">Version introduced</span></span>

<span data-ttu-id="a4a0f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a4a0f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a4a0f-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a4a0f-105">Old behavior</span></span>

<span data-ttu-id="a4a0f-106">L’appel `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` de méthode était le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="a4a0f-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a4a0f-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a4a0f-107">New behavior</span></span>

<span data-ttu-id="a4a0f-108">L’appel `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` de méthode est le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="a4a0f-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a4a0f-109">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="a4a0f-109">Reason for change</span></span>

<span data-ttu-id="a4a0f-110">Bootstrap 4 a été libéré au cours ASP.NET période de base 3.0.</span><span class="sxs-lookup"><span data-stu-id="a4a0f-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a4a0f-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a4a0f-111">Recommended action</span></span>

<span data-ttu-id="a4a0f-112">Vous êtes touché par ce changement si vous utilisez l’interface `Startup.ConfigureServices` utilisateur d’identité par défaut et l’avez ajouté comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a4a0f-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="a4a0f-113">Effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4a0f-113">Take one of the following actions:</span></span>

- <span data-ttu-id="a4a0f-114">Migrez votre application pour utiliser Bootstrap 4 à l’aide de leur [guide de migration](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="a4a0f-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="a4a0f-115">Mise `Startup.ConfigureServices` à jour pour faire respecter l’utilisation de Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="a4a0f-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="a4a0f-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a4a0f-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="a4a0f-117">Category</span><span class="sxs-lookup"><span data-stu-id="a4a0f-117">Category</span></span>

<span data-ttu-id="a4a0f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4a0f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a4a0f-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a4a0f-119">Affected APIs</span></span>

<span data-ttu-id="a4a0f-120">None</span><span class="sxs-lookup"><span data-stu-id="a4a0f-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
