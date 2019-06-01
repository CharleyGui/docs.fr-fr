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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91983a0910b272e621783f0fdb68242ddbd20f03
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456180"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="4aecd-102">\<UseRandomizedStringHashAlgorithm > élément</span><span class="sxs-lookup"><span data-stu-id="4aecd-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="4aecd-103">Détermine si le common language runtime calcule les codes de hachage pour les chaînes sur un domaine d’application par application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="4aecd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4aecd-104">\<configuration></span></span>  
<span data-ttu-id="4aecd-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="4aecd-105">\<runtime></span></span>  
<span data-ttu-id="4aecd-106">\<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="4aecd-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aecd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aecd-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aecd-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4aecd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4aecd-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4aecd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aecd-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4aecd-110">Attributes</span></span>  
  
|<span data-ttu-id="4aecd-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="4aecd-111">Attribute</span></span>|<span data-ttu-id="4aecd-112">Description</span><span class="sxs-lookup"><span data-stu-id="4aecd-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4aecd-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4aecd-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4aecd-114">Indique si les codes de hachage pour les chaînes sont calculés sur un domaine d’application par application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4aecd-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="4aecd-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4aecd-116">Value</span><span class="sxs-lookup"><span data-stu-id="4aecd-116">Value</span></span>|<span data-ttu-id="4aecd-117">Description</span><span class="sxs-lookup"><span data-stu-id="4aecd-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="4aecd-118">Le common language runtime ne calcule pas les codes de hachage pour les chaînes sur un par domaine d’application ; un algorithme unique est utilisé pour calculer les codes de hachage de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4aecd-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="4aecd-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4aecd-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="4aecd-120">Le common language runtime calcule les codes de hachage pour les chaînes sur un domaine d’application par application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="4aecd-121">Chaînes identiques dans différents domaines d’application et dans des processus différents auront différents codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="4aecd-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4aecd-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4aecd-122">Child Elements</span></span>  
 <span data-ttu-id="4aecd-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4aecd-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4aecd-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4aecd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4aecd-125">Élément</span><span class="sxs-lookup"><span data-stu-id="4aecd-125">Element</span></span>|<span data-ttu-id="4aecd-126">Description</span><span class="sxs-lookup"><span data-stu-id="4aecd-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4aecd-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4aecd-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4aecd-128">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="4aecd-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aecd-129">Notes</span><span class="sxs-lookup"><span data-stu-id="4aecd-129">Remarks</span></span>  
 <span data-ttu-id="4aecd-130">Par défaut, le <xref:System.StringComparer> classe et le <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode utilise un algorithme de hachage unique qui produit un code de hachage cohérent entre domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="4aecd-131">Cela revient à affecter la `enabled` attribut de la `<UseRandomizedStringHashAlgorithm>` élément à `0`.</span><span class="sxs-lookup"><span data-stu-id="4aecd-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="4aecd-132">Il s’agit de l’algorithme de hachage utilisé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4aecd-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="4aecd-133">Le <xref:System.StringComparer> classe et le <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode peut également utiliser un algorithme de hachage différent qui calcule les codes de hachage sur une par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="4aecd-134">Par conséquent, les codes de hachage des chaînes équivalentes varient entre domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="4aecd-135">Il s’agit d’une fonctionnalité d’abonnement ; Pour tirer parti de celui-ci, vous devez définir le `enabled` attribut de la `<UseRandomizedStringHashAlgorithm>` élément à `1`.</span><span class="sxs-lookup"><span data-stu-id="4aecd-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="4aecd-136">La recherche de chaîne dans une table de hachage est généralement une opération o (1).</span><span class="sxs-lookup"><span data-stu-id="4aecd-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="4aecd-137">Toutefois, quand un grand nombre de collisions se produire, la recherche peut devenir un O (n<sup>2</sup>) opération.</span><span class="sxs-lookup"><span data-stu-id="4aecd-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="4aecd-138">Vous pouvez utiliser le `<UseRandomizedStringHashAlgorithm>` élément de configuration à générer un algorithme de hachage aléatoire par domaine d’application, qui à son tour limite le nombre de collisions potentielles, en particulier quand les clés à partir de laquelle les codes de hachage sont calculés sont basées sur l’entrée de données par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="4aecd-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aecd-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="4aecd-139">Example</span></span>  
 <span data-ttu-id="4aecd-140">L’exemple suivant définit un `DisplayString` classe qui inclut une constante de chaîne privée, `s`, dont la valeur est « Il s’agit d’une chaîne. »</span><span class="sxs-lookup"><span data-stu-id="4aecd-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="4aecd-141">Il inclut également un `ShowStringHashCode` méthode qui affiche la valeur de chaîne et son code de hachage, ainsi que le nom du domaine d’application dans lequel la méthode s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4aecd-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="4aecd-142">Lorsque vous exécutez l’exemple sans fournir un fichier de configuration, il affiche une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="4aecd-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="4aecd-143">Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="4aecd-144">Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple et exécutez l’exemple, les codes de hachage pour la même chaîne diffèrent par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="4aecd-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4aecd-145">Lorsque le fichier de configuration est présent, l’exemple affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4aecd-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aecd-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4aecd-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
