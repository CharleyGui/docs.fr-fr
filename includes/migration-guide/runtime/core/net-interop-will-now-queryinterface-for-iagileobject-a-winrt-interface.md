---
ms.openlocfilehash: 65fa5d8629ce8e426cf1623590a056e5cad0b91f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497329"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a><span data-ttu-id="e74a9-101">.NET Interop effectue désormais un QI pour IAgileObject (interface WinRT)</span><span class="sxs-lookup"><span data-stu-id="e74a9-101">.NET Interop will now QueryInterface for IAgileObject (a WinRT interface)</span></span>

#### <a name="details"></a><span data-ttu-id="e74a9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e74a9-102">Details</span></span>

<span data-ttu-id="e74a9-103">Lorsque vous utilisez un événement WinRT avec un délégué .NET, Windows effectue un QI (QueryInterface) pour IAgileObject à compter de .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="e74a9-103">When using a WinRT event with a .NET delegate, Windows will QI for IAgileObject starting with the .NET Framework 4.8.</span></span>  <span data-ttu-id="e74a9-104">Dans les versions précédentes du .NET Framework, le runtime échouait et l’événement ne pouvait pas être inscrit.</span><span class="sxs-lookup"><span data-stu-id="e74a9-104">In previous versions of the .NET Framework, the runtime would fail that QI, and the event could not be subscribed.</span></span><ul><li><span data-ttu-id="e74a9-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="e74a9-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="e74a9-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e74a9-106">Suggestion</span></span>

<span data-ttu-id="e74a9-107">Si l’activation de QI pour IAgileObject arrête l’exécution, vous pouvez désactiver ce code en définissant la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="e74a9-107">If enabling the QI for IAgileObject breaks execution, you can disable this code by setting the following configuration.</span></span> <h4><span data-ttu-id="e74a9-108">Méthode 1 : variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="e74a9-108">Method 1: Environment variable</span></span></h4> <span data-ttu-id="e74a9-109">Définissez la variable d’environnement suivante : COMPLUS_DisableCCWSupportIAgileObject=1 Cette méthode affecte tout environnement héritant de cette variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="e74a9-109">Set the following environment variable:COMPLUS_DisableCCWSupportIAgileObject=1This method affects any environment that inherits this environment variable.</span></span> <span data-ttu-id="e74a9-110">Il peut s’agir d’une seule session de console, ou elle peut affecter l’ordinateur entier si vous définissez la variable d’environnement globalement.</span><span class="sxs-lookup"><span data-stu-id="e74a9-110">This might be just a single console session, or it might affect the entire machine if you set the environment variable globally.</span></span> <span data-ttu-id="e74a9-111">Le nom de la variable d’environnement n’est pas sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="e74a9-111">The environment variable name is not case-sensitive.</span></span> <h4><span data-ttu-id="e74a9-112">Méthode 2 : Registre</span><span class="sxs-lookup"><span data-stu-id="e74a9-112">Method 2: Registry</span></span></h4> <span data-ttu-id="e74a9-113">À l’aide de l’éditeur du Registre (regedit.exe), recherchez l’une des sous-clés suivantes : HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen ajoutez la valeur suivante : nom de la valeur : DisableCCWSupportIAgileObject type : DWORD (32-bit) value (également appelée REG_WORD) value : 1Vous pouvez utiliser l’outil de REG.EXE Windows pour ajouter cette valeur à partir d’un environnement de ligne de commande ou de script.</span><span class="sxs-lookup"><span data-stu-id="e74a9-113">Using Registry Editor (regedit.exe), find either of the following subkeys:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen add the following:Value name: DisableCCWSupportIAgileObject Type: DWORD (32-bit) Value (also called REG_WORD) Value: 1You can use the Windows REG.EXE tool to add this value from a command-line or scripting environment.</span></span> <span data-ttu-id="e74a9-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e74a9-114">For example:</span></span><pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre><span data-ttu-id="e74a9-115">Dans ce cas, <code>HKLM</code> peut être utilisé à la place de <code>HKEY_LOCAL_MACHINE</code>.</span><span class="sxs-lookup"><span data-stu-id="e74a9-115">In this case, <code>HKLM</code> is used instead of <code>HKEY_LOCAL_MACHINE</code>.</span></span> <span data-ttu-id="e74a9-116">Utilisez <code>reg add /?</code> pour afficher de l’aide sur cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e74a9-116">Use <code>reg add /?</code> to see help on this syntax.</span></span> <span data-ttu-id="e74a9-117">Le nom de la valeur de registre ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="e74a9-117">The registry value name is not case-sensitive.</span></span>

| <span data-ttu-id="e74a9-118">Name</span><span class="sxs-lookup"><span data-stu-id="e74a9-118">Name</span></span>    | <span data-ttu-id="e74a9-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="e74a9-119">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e74a9-120">Étendue</span><span class="sxs-lookup"><span data-stu-id="e74a9-120">Scope</span></span>   |<span data-ttu-id="e74a9-121">Edge</span><span class="sxs-lookup"><span data-stu-id="e74a9-121">Edge</span></span>|
|<span data-ttu-id="e74a9-122">Version</span><span class="sxs-lookup"><span data-stu-id="e74a9-122">Version</span></span>|<span data-ttu-id="e74a9-123">4.8</span><span class="sxs-lookup"><span data-stu-id="e74a9-123">4.8</span></span>|
|<span data-ttu-id="e74a9-124">Type</span><span class="sxs-lookup"><span data-stu-id="e74a9-124">Type</span></span>|<span data-ttu-id="e74a9-125">Runtime</span><span class="sxs-lookup"><span data-stu-id="e74a9-125">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e74a9-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="e74a9-126">Affected APIs</span></span>

<span data-ttu-id="e74a9-127">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="e74a9-127">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
