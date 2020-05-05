---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901888"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="ef777-101">Hébergement : l’hôte générique limite l’injection du constructeur de démarrage</span><span class="sxs-lookup"><span data-stu-id="ef777-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="ef777-102">Les seuls types que l’hôte générique prend `Startup` en charge pour l' `IHostEnvironment`injection `IWebHostEnvironment`de constructeur `IConfiguration`de classe sont, et.</span><span class="sxs-lookup"><span data-stu-id="ef777-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="ef777-103">Les applications `WebHost` utilisant ne sont pas affectées.</span><span class="sxs-lookup"><span data-stu-id="ef777-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ef777-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ef777-104">Change description</span></span>

<span data-ttu-id="ef777-105">Avant le ASP.NET Core 3,0, l’injection de constructeur pouvait être utilisée pour les types `Startup` arbitraires dans le constructeur de la classe.</span><span class="sxs-lookup"><span data-stu-id="ef777-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="ef777-106">Dans ASP.NET Core 3,0, la pile Web a été reconnectée à la bibliothèque d’hôte générique.</span><span class="sxs-lookup"><span data-stu-id="ef777-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="ef777-107">Vous pouvez voir la modification dans le fichier *Program.cs* des modèles :</span><span class="sxs-lookup"><span data-stu-id="ef777-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="ef777-108">**ASP.NET Core 2. x :**</span><span class="sxs-lookup"><span data-stu-id="ef777-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="ef777-109">**ASP.NET Core 3,0 :**</span><span class="sxs-lookup"><span data-stu-id="ef777-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="ef777-110">`Host`utilise un conteneur d’injection de dépendance (DI) pour générer l’application.</span><span class="sxs-lookup"><span data-stu-id="ef777-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="ef777-111">`WebHost`utilise deux conteneurs : un pour l’hôte et un pour l’application.</span><span class="sxs-lookup"><span data-stu-id="ef777-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="ef777-112">Par conséquent, le constructeur `Startup` ne prend plus en charge l’injection de service personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ef777-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="ef777-113">Seuls `IHostEnvironment`, `IWebHostEnvironment`et `IConfiguration` peuvent être injectés.</span><span class="sxs-lookup"><span data-stu-id="ef777-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="ef777-114">Cette modification empêche les problèmes de DI, tels que la création en double d’un service Singleton.</span><span class="sxs-lookup"><span data-stu-id="ef777-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef777-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ef777-115">Version introduced</span></span>

<span data-ttu-id="ef777-116">3.0</span><span class="sxs-lookup"><span data-stu-id="ef777-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ef777-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="ef777-117">Reason for change</span></span>

<span data-ttu-id="ef777-118">Cette modification est une conséquence de la replateforme de la pile Web sur la bibliothèque hôte générique.</span><span class="sxs-lookup"><span data-stu-id="ef777-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef777-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ef777-119">Recommended action</span></span>

<span data-ttu-id="ef777-120">Injectez des services `Startup.Configure` dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef777-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="ef777-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ef777-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="ef777-122">Category</span><span class="sxs-lookup"><span data-stu-id="ef777-122">Category</span></span>

<span data-ttu-id="ef777-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef777-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef777-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="ef777-124">Affected APIs</span></span>

<span data-ttu-id="ef777-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="ef777-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
