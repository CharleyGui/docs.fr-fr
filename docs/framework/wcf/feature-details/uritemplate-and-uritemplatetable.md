---
title: UriTemplate et UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 106ba21b58dabab96afbc8fb6db5cb305386f2fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595074"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="608df-102">UriTemplate et UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="608df-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="608df-103">Les développeurs de sites Web ont besoin de pouvoir décrire la forme et la disposition des URI auxquels leurs services répondent.</span><span class="sxs-lookup"><span data-stu-id="608df-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="608df-104">Windows Communication Foundation (WCF) a ajouté deux nouvelles classes pour permettre aux développeurs de contrôler leurs URI.</span><span class="sxs-lookup"><span data-stu-id="608df-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="608df-105"><xref:System.UriTemplate>et <xref:System.UriTemplateTable> constituent la base du moteur de répartition basé sur les URI dans WCF.</span><span class="sxs-lookup"><span data-stu-id="608df-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="608df-106">Ces classes peuvent également être utilisées de manière autonome, ce qui permet aux développeurs de tirer parti des modèles et du mécanisme de mappage d’URI sans implémenter de service WCF.</span><span class="sxs-lookup"><span data-stu-id="608df-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="608df-107">Modèles</span><span class="sxs-lookup"><span data-stu-id="608df-107">Templates</span></span>  
 <span data-ttu-id="608df-108">Un modèle est un moyen de décrire un ensemble d'URI relatifs.</span><span class="sxs-lookup"><span data-stu-id="608df-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="608df-109">L'ensemble de modèles URI présentés dans le tableau suivant montre comment peut être défini un système qui récupère différents types d'informations météorologiques.</span><span class="sxs-lookup"><span data-stu-id="608df-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="608df-110">Données</span><span class="sxs-lookup"><span data-stu-id="608df-110">Data</span></span>|<span data-ttu-id="608df-111">Modèle</span><span class="sxs-lookup"><span data-stu-id="608df-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="608df-112">Prévision par pays</span><span class="sxs-lookup"><span data-stu-id="608df-112">National Forecast</span></span>|<span data-ttu-id="608df-113">météo/pays</span><span class="sxs-lookup"><span data-stu-id="608df-113">weather/national</span></span>|  
|<span data-ttu-id="608df-114">Prévision par état</span><span class="sxs-lookup"><span data-stu-id="608df-114">State Forecast</span></span>|<span data-ttu-id="608df-115">météo/{état}</span><span class="sxs-lookup"><span data-stu-id="608df-115">weather/{state}</span></span>|  
|<span data-ttu-id="608df-116">Prévision par ville</span><span class="sxs-lookup"><span data-stu-id="608df-116">City Forecast</span></span>|<span data-ttu-id="608df-117">météo/{état}/{ville}</span><span class="sxs-lookup"><span data-stu-id="608df-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="608df-118">Prévision par activité</span><span class="sxs-lookup"><span data-stu-id="608df-118">Activity Forecast</span></span>|<span data-ttu-id="608df-119">météo/{état}/{ville}/{activité}</span><span class="sxs-lookup"><span data-stu-id="608df-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="608df-120">Cette table décrit un ensemble d'URI structurellement semblables.</span><span class="sxs-lookup"><span data-stu-id="608df-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="608df-121">Chaque entrée est un modèle URI.</span><span class="sxs-lookup"><span data-stu-id="608df-121">Each entry is a URI template.</span></span> <span data-ttu-id="608df-122">Les segments entre accolades décrivent des variables.</span><span class="sxs-lookup"><span data-stu-id="608df-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="608df-123">Les segments hors accolades décrivent des chaînes littérales.</span><span class="sxs-lookup"><span data-stu-id="608df-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="608df-124">Les classes de modèle WCF permettent à un développeur de prendre un URI entrant, par exemple « /Weather/wa/Seattle/Cycling », et de le faire correspondre à un modèle qui le décrit, « /Weather/{State}/{City}/{Activity} ».</span><span class="sxs-lookup"><span data-stu-id="608df-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="608df-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="608df-125">UriTemplate</span></span>  
 <span data-ttu-id="608df-126"><xref:System.UriTemplate> est une classe qui encapsule un modèle URI.</span><span class="sxs-lookup"><span data-stu-id="608df-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="608df-127">Le constructeur prend un paramètre de chaîne qui définit le modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="608df-128">Cette chaîne contient le modèle au format décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="608df-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="608df-129">La classe <xref:System.UriTemplate> fournit des méthodes qui vous permettent de faire correspondre un URI entrant à un modèle, de générer un URI a partir d'un modèle, de récupérer une collection de noms de variables utilisés dans le modèle, de déterminer si deux modèles sont équivalents et de retourner la chaîne du modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="608df-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> prend une adresse de base et un URI candidat et tente de faire correspondre l'URI au modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="608df-131">Si la correspondance est réussie, une instance <xref:System.UriTemplateMatch> est retournée.</span><span class="sxs-lookup"><span data-stu-id="608df-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="608df-132">L'objet <xref:System.UriTemplateMatch> contient un URI de base, l'URI candidat, une collection nom/valeur des paramètres de la requête, un tableau des segments du chemin d'accès relatif, une collection nom/valeur des variables mises en correspondance, l'instance <xref:System.UriTemplate> utilisée pour exécuter la correspondance, une chaîne contenant toute partie non appariée de l'URI candidat (utilisé lorsque le modèle comprend un caractère générique) et un objet associé au modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="608df-133">La classe <xref:System.UriTemplate> ignore le schéma et le numéro de port lors de la mise en correspondance d'un URI candidat à un modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="608df-134">Deux méthodes vous permettent de générer un URI à partir d'un modèle, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> et <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="608df-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="608df-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> prend une adresse de base et une collection nom/valeur de paramètres.</span><span class="sxs-lookup"><span data-stu-id="608df-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="608df-136">Ces paramètres sont substitués aux variables lorsque le modèle est lié.</span><span class="sxs-lookup"><span data-stu-id="608df-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="608df-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> prend les paires nom/valeur et les substitue de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="608df-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="608df-138"><xref:System.UriTemplate.ToString> retourne la chaîne du modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="608df-139">La propriété <xref:System.UriTemplate.PathSegmentVariableNames%2A> contient une collection des noms des variables utilisés dans les segments de chemin d’accès de la chaîne du modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="608df-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> prend <xref:System.UriTemplate> comme paramètre et retourne une valeur booléenne qui spécifie si les deux modèles sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="608df-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="608df-141">Pour plus d’informations, consultez la section équivalence des modèles plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="608df-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="608df-142"><xref:System.UriTemplate> est conçu pour utiliser tout schéma URI conforme à la grammaire d'URI HTTP.</span><span class="sxs-lookup"><span data-stu-id="608df-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="608df-143">Les éléments suivants illustrent des modèles URI pris en charge.</span><span class="sxs-lookup"><span data-stu-id="608df-143">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="608df-144">Des schémas tels que file:// et urn:// ne sont pas conformes à la grammaire d'URI HTTP et entraînent des résultats imprévisibles en cas d'utilisation avec les modèles URI.</span><span class="sxs-lookup"><span data-stu-id="608df-144">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="608df-145">Syntaxe de la chaîne du modèle</span><span class="sxs-lookup"><span data-stu-id="608df-145">Template String Syntax</span></span>  
 <span data-ttu-id="608df-146">Un modèle se compose de trois parties : un chemin d'accès, une requête facultative et un fragment facultatif.</span><span class="sxs-lookup"><span data-stu-id="608df-146">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="608df-147">Pour obtenir un exemple, consultez le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="608df-147">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="608df-148">Le chemin d'accès est "/météo/{état}/{ville}", la demande est "?prévision={durée}, et le fragment est "#frag1".</span><span class="sxs-lookup"><span data-stu-id="608df-148">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="608df-149">Les barres obliques de début et de fin sont facultatives dans l’expression du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="608df-149">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="608df-150">Les expressions de la requête et du fragment peuvent toutes deux être complètement omises.</span><span class="sxs-lookup"><span data-stu-id="608df-150">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="608df-151">Un chemin d’accès se compose d’une série de segments délimités par « / », chaque segment peut avoir une valeur littérale, un nom de variable (écrit entre {accolades}) ou un caractère générique (écrit comme « \* »).</span><span class="sxs-lookup"><span data-stu-id="608df-151">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="608df-152">Dans le modèle précédent, le segment "\météo\" est une valeur littérale tandis que "{état}" et "{ville}" sont des variables.</span><span class="sxs-lookup"><span data-stu-id="608df-152">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="608df-153">Les variables prennent leur nom à partir du contenu de leurs accolades et elles peuvent être remplacées ultérieurement par une valeur concrète pour créer un *URI fermé*.</span><span class="sxs-lookup"><span data-stu-id="608df-153">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="608df-154">Le caractère générique est facultatif, mais il ne peut figurer qu’à la fin de l’URI, où il correspond logiquement à « le reste du chemin d’accès ».</span><span class="sxs-lookup"><span data-stu-id="608df-154">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="608df-155">L’expression de requête, si elle est présente, spécifie une série de paires nom/valeur non ordonnées délimitées par' & '.</span><span class="sxs-lookup"><span data-stu-id="608df-155">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="608df-156">Les éléments de l'expression de la demande peuvent être des paires littérales (x=2) ou une paire variable (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="608df-156">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="608df-157">Seule la partie droite de la requête peut comporter une expression variable.</span><span class="sxs-lookup"><span data-stu-id="608df-157">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="608df-158">({Nom} = {Valeur} n'est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="608df-158">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="608df-159">Les valeurs non couplées (?x) ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="608df-159">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="608df-160">Il n'y a aucune différence entre une expression de demande vide et une expression de demande qui consiste en un '?' unique (les deux signifiant « aucune demande »).</span><span class="sxs-lookup"><span data-stu-id="608df-160">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="608df-161">L'expression du fragment peut se composer d'une valeur littérale ; aucune variable n'est autorisée.</span><span class="sxs-lookup"><span data-stu-id="608df-161">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="608df-162">Tous les noms de variables du modèle dans une chaîne de modèle doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="608df-162">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="608df-163">Les noms des variables du modèle ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="608df-163">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="608df-164">Exemples de chaînes de modèle valides :</span><span class="sxs-lookup"><span data-stu-id="608df-164">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="608df-165">""</span><span class="sxs-lookup"><span data-stu-id="608df-165">""</span></span>  
  
- <span data-ttu-id="608df-166">"/chaussure"</span><span class="sxs-lookup"><span data-stu-id="608df-166">"/shoe"</span></span>  
  
- <span data-ttu-id="608df-167">« /Shoe/ \* »</span><span class="sxs-lookup"><span data-stu-id="608df-167">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="608df-168">"{chaussure}/bateau"</span><span class="sxs-lookup"><span data-stu-id="608df-168">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="608df-169">« {sabot}/{Boat}/Bed/{Quilt} »</span><span class="sxs-lookup"><span data-stu-id="608df-169">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="608df-170">« chaussure/{bateau} »</span><span class="sxs-lookup"><span data-stu-id="608df-170">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="608df-171">« chaussure/{bateau}/ \* »</span><span class="sxs-lookup"><span data-stu-id="608df-171">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="608df-172">« chaussure/bateau ? x = 2 »</span><span class="sxs-lookup"><span data-stu-id="608df-172">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="608df-173">« chaussure/{bateau} ? x = {lit} »</span><span class="sxs-lookup"><span data-stu-id="608df-173">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="608df-174">« chaussure/{bateau} ? x = {lit} &y = bande »</span><span class="sxs-lookup"><span data-stu-id="608df-174">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="608df-175">" ? x = {chaussure}"</span><span class="sxs-lookup"><span data-stu-id="608df-175">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="608df-176">«chaussure ? x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="608df-176">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="608df-177">Exemples de chaînes de modèle non valides :</span><span class="sxs-lookup"><span data-stu-id="608df-177">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="608df-178">"{chaussure}/{SHOE}/x = 2" : noms de variables en double.</span><span class="sxs-lookup"><span data-stu-id="608df-178">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="608df-179">« {sabot}/Boat/ ? lit = {sabot} »-noms de variables en double.</span><span class="sxs-lookup"><span data-stu-id="608df-179">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="608df-180">" ? x = 2&x = 3" – les paires nom/valeur dans une chaîne de requête doivent être uniques, même s’il s’agit de littéraux.</span><span class="sxs-lookup"><span data-stu-id="608df-180">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="608df-181">" ? x = 2&" : la chaîne de requête est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="608df-181">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="608df-182">" ? 2&x = {chaussure}" – la chaîne de requête doit être une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="608df-182">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="608df-183">" ? y = 2&&X = 3" – la chaîne de requête doit être une paire de valeurs de nom, les noms ne peuvent pas commencer par' & '.</span><span class="sxs-lookup"><span data-stu-id="608df-183">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="608df-184">Segments de chemin d'accès composés</span><span class="sxs-lookup"><span data-stu-id="608df-184">Compound Path Segments</span></span>  
 <span data-ttu-id="608df-185">Les segments de chemin d’accès composés permettent à un segment du chemin d’accès de l’URI unique de contenir plusieurs variables ainsi que des variables associées à des littéraux.</span><span class="sxs-lookup"><span data-stu-id="608df-185">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="608df-186">Les éléments suivants illustrent des segments de chemin d’accès composés valides.</span><span class="sxs-lookup"><span data-stu-id="608df-186">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="608df-187">/nom_de_fichier.{ext}/</span><span class="sxs-lookup"><span data-stu-id="608df-187">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="608df-188">/{nom_de_fichier}.jpg/</span><span class="sxs-lookup"><span data-stu-id="608df-188">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="608df-189">/{nom_de_fichier}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="608df-189">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="608df-190">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="608df-190">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="608df-191">Les exemples suivants illustrent des segments de chemin d'accès non valides.</span><span class="sxs-lookup"><span data-stu-id="608df-191">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="608df-192">/ {} -Les variables doivent être nommées.</span><span class="sxs-lookup"><span data-stu-id="608df-192">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="608df-193">/{chaussure}{bateau} – Les variables doivent être séparées par un littéral.</span><span class="sxs-lookup"><span data-stu-id="608df-193">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="608df-194">Segments de chemin d'accès composés et correspondants</span><span class="sxs-lookup"><span data-stu-id="608df-194">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="608df-195">Les segments de chemin d’accès composés vous permettent de définit un modèle d’URI ayant plusieurs variables dans un seul segment de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="608df-195">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="608df-196">Par exemple, dans la chaîne de modèle suivante : "addresses/{State}. {City} "deux variables (State et City) sont définies dans le même segment.</span><span class="sxs-lookup"><span data-stu-id="608df-196">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="608df-197">Ce modèle correspondrait à une URL telle que, `http://example.com/Washington.Redmond` mais il correspondra également à une URL telle que `http://example.com/Washington.Redmond.Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="608df-197">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="608df-198">Dans ce dernier cas, la variable d’état contient « Washington » et la variable City contient « Redmond. Microsoft ».</span><span class="sxs-lookup"><span data-stu-id="608df-198">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="608df-199">Dans ce cas, tout texte (sauf ‘/’) correspondra à la variable {ville}.</span><span class="sxs-lookup"><span data-stu-id="608df-199">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="608df-200">Si vous souhaitez un modèle qui ne correspond pas au texte « supplémentaire », placez la variable dans un segment de modèle distinct, par exemple : « adresses/{État}/{City} ».</span><span class="sxs-lookup"><span data-stu-id="608df-200">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="608df-201">Segments de caractère générique nommés</span><span class="sxs-lookup"><span data-stu-id="608df-201">Named Wildcard Segments</span></span>  
 <span data-ttu-id="608df-202">Un segment de caractère générique nommé est tout segment variable de chemin d’accès dont le nom de variable commence par le caractère générique « \* ».</span><span class="sxs-lookup"><span data-stu-id="608df-202">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="608df-203">La chaîne de modèle suivante contient un segment de caractère générique nommé « chaussure ».</span><span class="sxs-lookup"><span data-stu-id="608df-203">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="608df-204">Les segments de caractère générique doivent respecter les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="608df-204">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="608df-205">Il peut y avoir tout au plus un segment de caractère générique nommé pour chaque chaîne de modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-205">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="608df-206">Un segment de caractère générique nommé doit apparaître à l’extrémité droite du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="608df-206">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="608df-207">Un segment de caractère générique nommé ne peut pas coexister avec un segment de caractère générique anonyme dans la même chaîne de modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-207">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="608df-208">Le nom d'un segment de caractère générique nommé doit être unique.</span><span class="sxs-lookup"><span data-stu-id="608df-208">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="608df-209">Les segments de caractère générique nommés ne peuvent pas comporter de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="608df-209">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="608df-210">Les segments de caractère générique nommés ne peuvent pas se terminer par « / ».</span><span class="sxs-lookup"><span data-stu-id="608df-210">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="608df-211">Valeurs de variables par défaut</span><span class="sxs-lookup"><span data-stu-id="608df-211">Default Variable Values</span></span>  
 <span data-ttu-id="608df-212">Les valeurs de variables par défaut vous permettent de spécifier les valeurs par défaut des variables dans un modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-212">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="608df-213">Les variables par défaut peuvent être spécifiées entre des accolades qui les déclarent ou comme une collection passée au constructeur UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="608df-213">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="608df-214">Le modèle suivant démontre deux méthodes pour spécifier un <xref:System.UriTemplate> comportant des variables avec des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="608df-214">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="608df-215">Ce modèle déclare une variable nommée `a` dont la valeur par défaut est `1` et une variable nommée `b` dont la valeur par défaut est `5`.</span><span class="sxs-lookup"><span data-stu-id="608df-215">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="608df-216">Seules les variables de segment de chemin d’accès peuvent avoir des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="608df-216">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="608df-217">Les variables de chaîne de requête, les variables de segments composés et les variables de caractère générique nommées ne peuvent pas avoir des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="608df-217">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="608df-218">Le code suivant montre comment les valeurs de variables par défaut sont gérées lors de la mise en correspondance d'un URI candidat.</span><span class="sxs-lookup"><span data-stu-id="608df-218">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="608df-219">Un URI tel que `http://localhost:8000///` ne correspond pas au modèle indiqué dans le code précédent, mais il s’agit d’un URI tel que `http://localhost:8000/` .</span><span class="sxs-lookup"><span data-stu-id="608df-219">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="608df-220">Le code suivant montre comment les valeurs de variables par défaut sont gérées à la création d'un URI avec un modèle.</span><span class="sxs-lookup"><span data-stu-id="608df-220">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
<span data-ttu-id="608df-221">Si une variable a une valeur par défaut `null`, quelques contraintes supplémentaires s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="608df-221">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="608df-222">Une variable peut avoir une valeur par défaut `null` si elle est contenue dans le segment qui se trouve à l'extrémité droite de la chaîne de modèle ou si tous les segments à droite du segment ont des valeurs par défaut `null`.</span><span class="sxs-lookup"><span data-stu-id="608df-222">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="608df-223">Les exemples suivants illustrent des chaînes de modèle comportant des valeurs par défaut `null` valides :</span><span class="sxs-lookup"><span data-stu-id="608df-223">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="608df-224">Voici les chaînes de modèle non valides avec les valeurs par défaut `null` :</span><span class="sxs-lookup"><span data-stu-id="608df-224">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="608df-225">Valeurs par défaut et correspondance</span><span class="sxs-lookup"><span data-stu-id="608df-225">Default Values and Matching</span></span>  
 <span data-ttu-id="608df-226">Lorsque vous mettez en correspondance un URI candidat avec un modèle comportant des valeurs par défaut, si des valeurs ne sont pas spécifiées dans l’URI candidat, les valeurs par défaut seront placées dans la collection <xref:System.UriTemplateMatch.BoundVariables%2A>.</span><span class="sxs-lookup"><span data-stu-id="608df-226">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="608df-227">Équivalence des modèles</span><span class="sxs-lookup"><span data-stu-id="608df-227">Template Equivalence</span></span>  
 <span data-ttu-id="608df-228">Deux modèles sont dits de *structure équivalente* lorsque tous les littéraux des modèles correspondent et qu’ils ont des variables dans les mêmes segments.</span><span class="sxs-lookup"><span data-stu-id="608df-228">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="608df-229">Par exemple, les deux modèles suivants sont structurellement équivalents :</span><span class="sxs-lookup"><span data-stu-id="608df-229">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="608df-230">/a/{var1}/b b/{var2} ? x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="608df-230">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="608df-231">a/{x}/b% 20B/{var1} ? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="608df-231">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="608df-232">a/{y}/B% 20B/{z}/ ? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="608df-232">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="608df-233">Quelques points à noter :</span><span class="sxs-lookup"><span data-stu-id="608df-233">A few things to notice:</span></span>  
  
- <span data-ttu-id="608df-234">Si un modèle contient des barres obliques de début, seule la première est ignorée.</span><span class="sxs-lookup"><span data-stu-id="608df-234">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="608df-235">Lors de la comparaison des chaînes de modèles pour rechercher une équivalence structurelle, la casse est ignorée pour les noms de variables et les segments de chemin d’accès, mais les chaînes de demande respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="608df-235">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="608df-236">Les chaînes de demande ne sont pas ordonnées.</span><span class="sxs-lookup"><span data-stu-id="608df-236">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="608df-237">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="608df-237">UriTemplateTable</span></span>  
 <span data-ttu-id="608df-238">La classe <xref:System.UriTemplateTable> représente une table associative d'objets <xref:System.UriTemplate> liés à un objet choisi par le développeur.</span><span class="sxs-lookup"><span data-stu-id="608df-238">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="608df-239">Une <xref:System.UriTemplateTable> doit contenir au moins un <xref:System.UriTemplate> avant d'appeler <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="608df-239">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="608df-240">Le contenu d'une  <xref:System.UriTemplateTable> peut être modifié jusqu'à l'appel de <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="608df-240">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="608df-241">La validation est exécutée lorsque <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée.</span><span class="sxs-lookup"><span data-stu-id="608df-241">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="608df-242">Le type de validation exécuté dépend de la valeur du paramètre `allowMultiple` de <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="608df-242">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="608df-243">Lorsque <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée en passant `false`, la <xref:System.UriTemplateTable> vérifie qu'il n'y a pas de modèle dans la table.</span><span class="sxs-lookup"><span data-stu-id="608df-243">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="608df-244">Si elle recherche des modèles structurellement équivalents, elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="608df-244">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="608df-245">À utiliser conjointement avec <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> lorsque vous souhaitez garantir qu'un seul modèle correspond à un URI entrant.</span><span class="sxs-lookup"><span data-stu-id="608df-245">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="608df-246">Si <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée en passant dans `true`, <xref:System.UriTemplateTable> autorise la présence de plusieurs modèles structurellement équivalents dans une <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="608df-246">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="608df-247">Si un ensemble d'objets <xref:System.UriTemplate> ajoutés à une <xref:System.UriTemplateTable> contiennent des chaînes de demande, ils ne doivent pas être ambigus.</span><span class="sxs-lookup"><span data-stu-id="608df-247">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="608df-248">Les chaînes de demande identiques sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="608df-248">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="608df-249">Alors que la <xref:System.UriTemplateTable> accepte les adresses de base utilisant des schémas autres que HTTP, le schéma et le numéro de port sont ignorés lors de la mise en correspondance des URI candidats avec les modèles.</span><span class="sxs-lookup"><span data-stu-id="608df-249">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="608df-250">Ambiguïté des chaînes de demande</span><span class="sxs-lookup"><span data-stu-id="608df-250">Query String Ambiguity</span></span>  
 <span data-ttu-id="608df-251">Les modèles qui partagent un chemin d’accès équivalent contiennent des chaînes de demande ambiguës si un URI correspond à plusieurs modèles.</span><span class="sxs-lookup"><span data-stu-id="608df-251">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="608df-252">Les ensembles suivants de chaînes de requête ne sont pas ambigus entre eux :</span><span class="sxs-lookup"><span data-stu-id="608df-252">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="608df-253">?x=1</span><span class="sxs-lookup"><span data-stu-id="608df-253">?x=1</span></span>  
  
- <span data-ttu-id="608df-254">?x=2</span><span class="sxs-lookup"><span data-stu-id="608df-254">?x=2</span></span>  
  
- <span data-ttu-id="608df-255">?x=3</span><span class="sxs-lookup"><span data-stu-id="608df-255">?x=3</span></span>  
  
- <span data-ttu-id="608df-256">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="608df-256">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="608df-257">? x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="608df-257">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="608df-258">?x=3</span><span class="sxs-lookup"><span data-stu-id="608df-258">?x=3</span></span>  
  
- <span data-ttu-id="608df-259">?x=1</span><span class="sxs-lookup"><span data-stu-id="608df-259">?x=1</span></span>  
  
- <span data-ttu-id="608df-260">?</span><span class="sxs-lookup"><span data-stu-id="608df-260">?</span></span>  
  
- <span data-ttu-id="608df-261">?</span><span class="sxs-lookup"><span data-stu-id="608df-261">?</span></span> <span data-ttu-id="608df-262">x={var}</span><span class="sxs-lookup"><span data-stu-id="608df-262">x={var}</span></span>  
  
- <span data-ttu-id="608df-263">?</span><span class="sxs-lookup"><span data-stu-id="608df-263">?</span></span>  
  
- <span data-ttu-id="608df-264">? m = obtient&c = RSS</span><span class="sxs-lookup"><span data-stu-id="608df-264">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="608df-265">? m = put&c = RSS</span><span class="sxs-lookup"><span data-stu-id="608df-265">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="608df-266">? m = obtient&c = Atom</span><span class="sxs-lookup"><span data-stu-id="608df-266">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="608df-267">? m = put&c = Atom</span><span class="sxs-lookup"><span data-stu-id="608df-267">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="608df-268">Les ensembles suivants de modèles de chaînes de requête sont ambigus entre eux :</span><span class="sxs-lookup"><span data-stu-id="608df-268">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="608df-269">?x=1</span><span class="sxs-lookup"><span data-stu-id="608df-269">?x=1</span></span>  
  
- <span data-ttu-id="608df-270">?x={var}</span><span class="sxs-lookup"><span data-stu-id="608df-270">?x={var}</span></span>  
  
 <span data-ttu-id="608df-271">"x=1" - correspond aux deux modèles.</span><span class="sxs-lookup"><span data-stu-id="608df-271">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="608df-272">?x=1</span><span class="sxs-lookup"><span data-stu-id="608df-272">?x=1</span></span>  
  
- <span data-ttu-id="608df-273">?y=2</span><span class="sxs-lookup"><span data-stu-id="608df-273">?y=2</span></span>  
  
 <span data-ttu-id="608df-274">"x = 1&y = 2" correspond aux deux modèles.</span><span class="sxs-lookup"><span data-stu-id="608df-274">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="608df-275">C'est parce qu'une chaîne de demande peut contenir plus de variables de chaîne de demande que le modèle auquel elle correspond.</span><span class="sxs-lookup"><span data-stu-id="608df-275">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="608df-276">?x=1</span><span class="sxs-lookup"><span data-stu-id="608df-276">?x=1</span></span>  
  
- <span data-ttu-id="608df-277">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="608df-277">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="608df-278">"x = 1&y = 3" correspond aux deux modèles.</span><span class="sxs-lookup"><span data-stu-id="608df-278">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="608df-279">? x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="608df-279">?x=3&y=4</span></span>  
  
- <span data-ttu-id="608df-280">? x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="608df-280">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="608df-281">Les caractères á et Á sont considérés comme des caractères différents lorsqu'ils apparaissent dans le cadre d'un chemin d'accès d'URI ou d'un littéral de segment de chemin d'accès <xref:System.UriTemplate> (en revanche, les caractères a et A sont considérés comme identiques).</span><span class="sxs-lookup"><span data-stu-id="608df-281">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="608df-282">Les caractères á et Á sont considérés comme identiques lorsqu'ils apparaissent dans le cadre d'un {nomVariable} <xref:System.UriTemplate> ou d'une chaîne de demande (a et A sont également considérés comme identiques).</span><span class="sxs-lookup"><span data-stu-id="608df-282">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608df-283">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="608df-283">See also</span></span>

- [<span data-ttu-id="608df-284">Vue d'ensemble du modèle de programmation Web HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="608df-284">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="608df-285">Modèle objet de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="608df-285">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="608df-286">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="608df-286">UriTemplate</span></span>](../samples/uritemplate-sample.md)
- [<span data-ttu-id="608df-287">Table UriTemplate</span><span class="sxs-lookup"><span data-stu-id="608df-287">UriTemplate Table</span></span>](../samples/uritemplate-table-sample.md)
- [<span data-ttu-id="608df-288">Répartiteur de table UriTemplate</span><span class="sxs-lookup"><span data-stu-id="608df-288">UriTemplate Table Dispatcher</span></span>](../samples/uritemplate-table-dispatcher-sample.md)
