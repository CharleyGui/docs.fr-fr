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
ms.openlocfilehash: 148d55c8b8a63737867c4bfdf3ab118dfdefd6f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174093"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="360e1-102">Élément \<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="360e1-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>

<span data-ttu-id="360e1-103">Détermine si le common language runtime calcule les codes de hachage pour les chaînes par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="360e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="360e1-104">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="360e1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="360e1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="360e1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="360e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="360e1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="360e1-107">Attributes</span></span>  
  
|<span data-ttu-id="360e1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="360e1-108">Attribute</span></span>|<span data-ttu-id="360e1-109">Description</span><span class="sxs-lookup"><span data-stu-id="360e1-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="360e1-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="360e1-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="360e1-111">Spécifie si les codes de hachage pour les chaînes sont calculés par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-111">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="360e1-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="360e1-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="360e1-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="360e1-113">Value</span></span>|<span data-ttu-id="360e1-114">Description</span><span class="sxs-lookup"><span data-stu-id="360e1-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="360e1-115">Le common language runtime ne calcule pas les codes de hachage pour les chaînes par domaine d’application ; un seul algorithme est utilisé pour calculer les codes de hachage de chaîne.</span><span class="sxs-lookup"><span data-stu-id="360e1-115">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="360e1-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="360e1-116">This is the default.</span></span>|  
|`1`|<span data-ttu-id="360e1-117">Le common language runtime calcule les codes de hachage pour les chaînes par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-117">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="360e1-118">Les chaînes identiques dans différents domaines d’application et dans des processus différents auront des codes de hachage différents.</span><span class="sxs-lookup"><span data-stu-id="360e1-118">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="360e1-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="360e1-119">Child Elements</span></span>  

 <span data-ttu-id="360e1-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="360e1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="360e1-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="360e1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="360e1-122">Élément</span><span class="sxs-lookup"><span data-stu-id="360e1-122">Element</span></span>|<span data-ttu-id="360e1-123">Description</span><span class="sxs-lookup"><span data-stu-id="360e1-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="360e1-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="360e1-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="360e1-125">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="360e1-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="360e1-126">Notes</span><span class="sxs-lookup"><span data-stu-id="360e1-126">Remarks</span></span>  

 <span data-ttu-id="360e1-127">Par défaut, la <xref:System.StringComparer> classe et la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode utilisent un algorithme de hachage unique qui produit un code de hachage cohérent entre les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-127">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="360e1-128">Cela équivaut à affecter à l' `enabled` attribut de l' `<UseRandomizedStringHashAlgorithm>` élément la valeur `0` .</span><span class="sxs-lookup"><span data-stu-id="360e1-128">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="360e1-129">Il s’agit de l’algorithme de hachage utilisé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="360e1-129">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="360e1-130">La <xref:System.StringComparer> classe et la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode peuvent également utiliser un algorithme de hachage différent qui calcule les codes de hachage pour chaque domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-130">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="360e1-131">Par conséquent, les codes de hachage pour les chaînes équivalentes diffèrent entre les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="360e1-131">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="360e1-132">Il s’agit d’une fonctionnalité d’abonnement. pour en tirer parti, vous devez affecter la valeur à l' `enabled` attribut de l' `<UseRandomizedStringHashAlgorithm>` élément `1` .</span><span class="sxs-lookup"><span data-stu-id="360e1-132">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="360e1-133">La recherche de chaîne dans une table de hachage est généralement une opération O (1).</span><span class="sxs-lookup"><span data-stu-id="360e1-133">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="360e1-134">Toutefois, lorsqu’un grand nombre de collisions se produisent, la recherche peut devenir une opération O (n<sup>2</sup>).</span><span class="sxs-lookup"><span data-stu-id="360e1-134">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="360e1-135">Vous pouvez utiliser l' `<UseRandomizedStringHashAlgorithm>` élément de configuration pour générer un algorithme de hachage aléatoire par domaine d’application, qui, à son tour, limite le nombre de collisions potentielles, en particulier lorsque les clés à partir desquelles les codes de hachage sont calculés sont basées sur les données entrées par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="360e1-135">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="360e1-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="360e1-136">Example</span></span>  

 <span data-ttu-id="360e1-137">L’exemple suivant définit une `DisplayString` classe qui comprend une constante de chaîne privée, `s` , dont la valeur est « This is a String ».</span><span class="sxs-lookup"><span data-stu-id="360e1-137">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="360e1-138">Il inclut également une méthode `ShowStringHashCode` qui affiche la valeur de chaîne et son code de hachage avec le nom du domaine d'application dans lequel la méthode est exécutée.</span><span class="sxs-lookup"><span data-stu-id="360e1-138">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="360e1-139">Lorsque vous exécutez l'exemple sans fournir un fichier de configuration, il affiche une sortie similaire à la suivante.</span><span class="sxs-lookup"><span data-stu-id="360e1-139">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="360e1-140">Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="360e1-140">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="360e1-141">Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l'exemple, puis exécutez l'exemple, les codes de hachage pour la même chaîne diffèrent par domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="360e1-141">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="360e1-142">Lorsque le fichier de configuration est présent, l'exemple affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="360e1-142">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="360e1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="360e1-143">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
