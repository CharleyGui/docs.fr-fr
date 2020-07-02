---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614430"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="25909-101">appels aux constructeurs ClaimsIdentity</span><span class="sxs-lookup"><span data-stu-id="25909-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="25909-102">Détails</span><span class="sxs-lookup"><span data-stu-id="25909-102">Details</span></span>

<span data-ttu-id="25909-103">À compter de .NET Framework 4.6.2, la façon dont les constructeurs <xref:System.Security.Claims.ClaimsIdentity> avec un paramètre <xref:System.Security.Principal.IIdentity?displayProperty=fullName> définissent la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est modifiée.</span><span class="sxs-lookup"><span data-stu-id="25909-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="25909-104">Si l’argument <xref:System.Security.Principal.IIdentity?displayProperty=fullName> est un objet <xref:System.Security.Claims.ClaimsIdentity> et que la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> de cet objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas `null`, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est attachée à l’aide de la méthode <xref:System.Security.Claims.ClaimsIdentity.Clone>.</span><span class="sxs-lookup"><span data-stu-id="25909-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="25909-105">Dans Framework 4.6.1 et les versions antérieures, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est jointe comme une référence existante. En raison de ce changement, à compter de .NET Framework 4.6.2, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> du nouvel objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas égale à la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> de l’argument <xref:System.Security.Principal.IIdentity?displayProperty=fullName> du constructeur.</span><span class="sxs-lookup"><span data-stu-id="25909-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="25909-106">Dans .NET Framework 4.6.1 et les versions antérieures, elle est égale.</span><span class="sxs-lookup"><span data-stu-id="25909-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25909-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="25909-107">Suggestion</span></span>

<span data-ttu-id="25909-108">Si ce comportement n’est pas souhaitable, vous pouvez restaurer le comportement précédent en réglant `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` dans votre fichier de configuration d’application sur `true`.</span><span class="sxs-lookup"><span data-stu-id="25909-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="25909-109">Pour cela, vous ajoutez le code suivant à la section `<runtime>` de votre fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="25909-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="25909-110">Nom</span><span class="sxs-lookup"><span data-stu-id="25909-110">Name</span></span>    | <span data-ttu-id="25909-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="25909-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25909-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="25909-112">Scope</span></span>   | <span data-ttu-id="25909-113">Edge</span><span class="sxs-lookup"><span data-stu-id="25909-113">Edge</span></span>        |
| <span data-ttu-id="25909-114">Version</span><span class="sxs-lookup"><span data-stu-id="25909-114">Version</span></span> | <span data-ttu-id="25909-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="25909-115">4.6.2</span></span>       |
| <span data-ttu-id="25909-116">Type</span><span class="sxs-lookup"><span data-stu-id="25909-116">Type</span></span>    | <span data-ttu-id="25909-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="25909-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="25909-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="25909-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
