---
ms.openlocfilehash: ceae6b85c14862b1b1183d01def0dda723ee0c2b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496824"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="11f86-101">EF ne lève plus d’exception pour des QueryView avec des caractéristiques spécifiques</span><span class="sxs-lookup"><span data-stu-id="11f86-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="11f86-102">Détails</span><span class="sxs-lookup"><span data-stu-id="11f86-102">Details</span></span>

<span data-ttu-id="11f86-103">Entity Framework ne lève plus une exception <xref:System.StackOverflowException?displayProperty=fullName> quand une application exécute une requête qui implique un QueryView avec une propriété de navigation 0..1 qui tente d’inclure les entités associées dans le cadre de la requête,</span><span class="sxs-lookup"><span data-stu-id="11f86-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="11f86-104">par exemple en appelant <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="11f86-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="11f86-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="11f86-105">Suggestion</span></span>

<span data-ttu-id="11f86-106">Cette modification affecte uniquement le code qui utilise des QueryView avec des relations 1-0..1 pour exécuter des requêtes qui appellent .Include.</span><span class="sxs-lookup"><span data-stu-id="11f86-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="11f86-107">Elle permet d'améliorer la fiabilité et doit être transparente pour presque toutes les applications.</span><span class="sxs-lookup"><span data-stu-id="11f86-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="11f86-108">Toutefois, si elle entraîne un comportement inattendu, vous pouvez la désactiver en ajoutant l'entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l'application :</span><span class="sxs-lookup"><span data-stu-id="11f86-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="11f86-109">Name</span><span class="sxs-lookup"><span data-stu-id="11f86-109">Name</span></span>    | <span data-ttu-id="11f86-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="11f86-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="11f86-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="11f86-111">Scope</span></span>   |<span data-ttu-id="11f86-112">Edge</span><span class="sxs-lookup"><span data-stu-id="11f86-112">Edge</span></span>|
|<span data-ttu-id="11f86-113">Version</span><span class="sxs-lookup"><span data-stu-id="11f86-113">Version</span></span>|<span data-ttu-id="11f86-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="11f86-114">4.5.2</span></span>|
|<span data-ttu-id="11f86-115">Type</span><span class="sxs-lookup"><span data-stu-id="11f86-115">Type</span></span>|<span data-ttu-id="11f86-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="11f86-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="11f86-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="11f86-117">Affected APIs</span></span>

<span data-ttu-id="11f86-118">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="11f86-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
