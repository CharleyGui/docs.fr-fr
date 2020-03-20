---
title: Élément <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153775"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="49931-102">\<UtilisationRandomizedStringHashAlgorithm> Element</span><span class="sxs-lookup"><span data-stu-id="49931-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="49931-103">Détermine si le temps d’exécution de langue commun calcule des codes de hachage pour les chaînes sur une base de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="49931-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="49931-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="49931-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="49931-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="49931-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="49931-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UtilisationRandomizedStringHashAlgorithm>**</span><span class="sxs-lookup"><span data-stu-id="49931-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49931-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49931-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49931-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="49931-108">Attributes and Elements</span></span>  
 <span data-ttu-id="49931-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="49931-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49931-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="49931-110">Attributes</span></span>  
  
|<span data-ttu-id="49931-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="49931-111">Attribute</span></span>|<span data-ttu-id="49931-112">Description</span><span class="sxs-lookup"><span data-stu-id="49931-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="49931-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="49931-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="49931-114">Précise si les codes de hachage pour les chaînes sont calculés sur une base de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="49931-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="49931-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="49931-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="49931-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="49931-116">Value</span></span>|<span data-ttu-id="49931-117">Description</span><span class="sxs-lookup"><span data-stu-id="49931-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="49931-118">L’heure courante de fonctionnement de langue ne calcule pas des codes de hachage pour des chaînes sur une base de domaine d’application ; un seul algorithme est utilisé pour calculer les codes de hachage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="49931-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="49931-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="49931-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="49931-120">Le langage courant calcule des codes de hachage pour les chaînes par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="49931-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="49931-121">Les chaînes identiques dans différents domaines d’application et dans différents processus auront différents codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="49931-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49931-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="49931-122">Child Elements</span></span>  
 <span data-ttu-id="49931-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="49931-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49931-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="49931-124">Parent Elements</span></span>  
  
|<span data-ttu-id="49931-125">Élément</span><span class="sxs-lookup"><span data-stu-id="49931-125">Element</span></span>|<span data-ttu-id="49931-126">Description</span><span class="sxs-lookup"><span data-stu-id="49931-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="49931-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49931-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="49931-128">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="49931-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49931-129">Notes </span><span class="sxs-lookup"><span data-stu-id="49931-129">Remarks</span></span>  
 <span data-ttu-id="49931-130">Par défaut, <xref:System.StringComparer> la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> classe et la méthode utilisent un algorithme de hachage unique qui produit un code de hachage cohérent dans tous les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="49931-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="49931-131">Cela équivaut à `enabled` définir `<UseRandomizedStringHashAlgorithm>` l’attribut de l’élément à `0`.</span><span class="sxs-lookup"><span data-stu-id="49931-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="49931-132">Il s’agit de l’algorithme de hachage utilisé dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="49931-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="49931-133">La <xref:System.StringComparer> classe <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> et la méthode peuvent également utiliser un algorithme de hachage différent qui calcule les codes de hachage sur une base de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="49931-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="49931-134">Par conséquent, les codes de hachage pour les chaînes équivalentes varieront d’un domaine d’application à l’autre.</span><span class="sxs-lookup"><span data-stu-id="49931-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="49931-135">Il s’agit d’une fonction d’opt-in; pour en profiter, vous devez `enabled` définir `<UseRandomizedStringHashAlgorithm>` l’attribut de l’élément à `1`.</span><span class="sxs-lookup"><span data-stu-id="49931-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="49931-136">Le lookup de chaîne dans une table de hachage est typiquement une opération O(1).</span><span class="sxs-lookup"><span data-stu-id="49931-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="49931-137">Cependant, lorsqu’un grand nombre de collisions se produisent, la recherche peut devenir une opération O(n<sup>2).</sup></span><span class="sxs-lookup"><span data-stu-id="49931-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="49931-138">Vous pouvez `<UseRandomizedStringHashAlgorithm>` utiliser l’élément de configuration pour générer un algorithme aléatoire de hachage par domaine d’application, ce qui limite à son tour le nombre de collisions potentielles, en particulier lorsque les clés à partir desquelles les codes de hachage sont calculés sont basées sur l’entrée de données par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="49931-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49931-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="49931-139">Example</span></span>  
 <span data-ttu-id="49931-140">L’exemple suivant `DisplayString` définit une classe qui `s`comprend une constante de cordes privées, dont la valeur est "C’est une chaîne."</span><span class="sxs-lookup"><span data-stu-id="49931-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="49931-141">Il inclut également une méthode `ShowStringHashCode` qui affiche la valeur de chaîne et son code de hachage avec le nom du domaine d'application dans lequel la méthode est exécutée.</span><span class="sxs-lookup"><span data-stu-id="49931-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="49931-142">Lorsque vous exécutez l'exemple sans fournir un fichier de configuration, il affiche une sortie similaire à la suivante.</span><span class="sxs-lookup"><span data-stu-id="49931-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="49931-143">Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="49931-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="49931-144">Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l'exemple, puis exécutez l'exemple, les codes de hachage pour la même chaîne diffèrent par domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="49931-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="49931-145">Lorsque le fichier de configuration est présent, l'exemple affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="49931-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="49931-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49931-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
