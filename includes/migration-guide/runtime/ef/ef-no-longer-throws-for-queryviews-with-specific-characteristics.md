---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620027"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="987e7-101">EF ne lève plus d’exception pour des QueryView avec des caractéristiques spécifiques</span><span class="sxs-lookup"><span data-stu-id="987e7-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="987e7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="987e7-102">Details</span></span>

<span data-ttu-id="987e7-103">Entity Framework ne lève plus une exception <xref:System.StackOverflowException?displayProperty=fullName> quand une application exécute une requête qui implique un QueryView avec une propriété de navigation 0..1 qui tente d’inclure les entités associées dans le cadre de la requête,</span><span class="sxs-lookup"><span data-stu-id="987e7-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="987e7-104">par exemple en appelant <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="987e7-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="987e7-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="987e7-105">Suggestion</span></span>

<span data-ttu-id="987e7-106">Cette modification affecte uniquement le code qui utilise des QueryView avec des relations 1-0..1 pour exécuter des requêtes qui appellent .Include.</span><span class="sxs-lookup"><span data-stu-id="987e7-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="987e7-107">Elle permet d'améliorer la fiabilité et doit être transparente pour presque toutes les applications.</span><span class="sxs-lookup"><span data-stu-id="987e7-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="987e7-108">Toutefois, si elle entraîne un comportement inattendu, vous pouvez la désactiver en ajoutant l'entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l'application :</span><span class="sxs-lookup"><span data-stu-id="987e7-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="987e7-109">Nom</span><span class="sxs-lookup"><span data-stu-id="987e7-109">Name</span></span>    | <span data-ttu-id="987e7-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="987e7-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="987e7-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="987e7-111">Scope</span></span>   |<span data-ttu-id="987e7-112">Edge</span><span class="sxs-lookup"><span data-stu-id="987e7-112">Edge</span></span>|
|<span data-ttu-id="987e7-113">Version</span><span class="sxs-lookup"><span data-stu-id="987e7-113">Version</span></span>|<span data-ttu-id="987e7-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="987e7-114">4.5.2</span></span>|
|<span data-ttu-id="987e7-115">Type</span><span class="sxs-lookup"><span data-stu-id="987e7-115">Type</span></span>|<span data-ttu-id="987e7-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="987e7-116">Runtime</span></span>|
