---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614446"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="23752-101">Vérifier que System.Uri utilise un jeu de caractères réservés cohérent</span><span class="sxs-lookup"><span data-stu-id="23752-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="23752-102">Détails</span><span class="sxs-lookup"><span data-stu-id="23752-102">Details</span></span>

<span data-ttu-id="23752-103">Dans <xref:System.Uri?displayProperty=fullName>, certains caractères encodés en pourcentage qui étaient parfois décodés demeurent désormais systématiquement encodés.</span><span class="sxs-lookup"><span data-stu-id="23752-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="23752-104">Cela se produit sur les propriétés et méthodes qui accèdent aux composants de chemin, de requête, de fragment ou d’informations utilisateur de l’URI.</span><span class="sxs-lookup"><span data-stu-id="23752-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="23752-105">Le comportement change uniquement quand les deux conditions suivantes sont vraies :</span><span class="sxs-lookup"><span data-stu-id="23752-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="23752-106">L’URI contient la forme encodée d’un des caractères réservés suivants : `:`, `'`, `(`, `)`, `!` ou `*`.</span><span class="sxs-lookup"><span data-stu-id="23752-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="23752-107">L’URI contient un caractère non réservé encodé ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="23752-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="23752-108">Si les deux conditions ci-dessus sont remplies, les caractères réservés encodés demeurent encodés.</span><span class="sxs-lookup"><span data-stu-id="23752-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="23752-109">Dans les versions précédentes du .NET Framework, ils sont décodés.</span><span class="sxs-lookup"><span data-stu-id="23752-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23752-110">Suggestion</span><span class="sxs-lookup"><span data-stu-id="23752-110">Suggestion</span></span>

<span data-ttu-id="23752-111">Pour les applications qui ciblent les versions du .NET Framework à partir de la version 4.7.2, le nouveau comportement de décodage est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="23752-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="23752-112">Si ce changement n’est pas souhaitable, vous pouvez le désactiver en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="23752-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="23752-113">Pour les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur .NET Framework versions 4.7.2 et ultérieures, le nouveau comportement de décodage est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="23752-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="23752-114">Vous pouvez l’activer en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la `<runtime>` section du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="23752-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="23752-115">Nom</span><span class="sxs-lookup"><span data-stu-id="23752-115">Name</span></span>    | <span data-ttu-id="23752-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="23752-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23752-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="23752-117">Scope</span></span>   | <span data-ttu-id="23752-118">Secondaire</span><span class="sxs-lookup"><span data-stu-id="23752-118">Minor</span></span>       |
| <span data-ttu-id="23752-119">Version</span><span class="sxs-lookup"><span data-stu-id="23752-119">Version</span></span> | <span data-ttu-id="23752-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="23752-120">4.7.2</span></span>       |
| <span data-ttu-id="23752-121">Type</span><span class="sxs-lookup"><span data-stu-id="23752-121">Type</span></span>    | <span data-ttu-id="23752-122">Reciblage</span><span class="sxs-lookup"><span data-stu-id="23752-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="23752-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="23752-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
