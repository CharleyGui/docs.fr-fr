---
title: Exécution de changements de casse indépendants de la culture
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276814"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="dbdb5-102">Exécution de changements de casse indépendants de la culture</span><span class="sxs-lookup"><span data-stu-id="dbdb5-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="dbdb5-103">Les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> fournissent des surcharges qui n’acceptent pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="dbdb5-104">Par défaut, ces surcharges sans paramètres effectuent des changements de casse basés sur la valeur de la <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dbdb5-105">Cela produit des résultats de la casse qui peuvent varier selon la culture.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="dbdb5-106">Pour indiquer clairement si vous souhaitez que les changements de casse soient ou non dépendants de la culture, vous devez utiliser les surcharges de ces méthodes qui vous demandent de spécifier explicitement un paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="dbdb5-107">Pour les changements de casse dépendants de la culture, spécifiez `CultureInfo.CurrentCulture` pour le paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="dbdb5-108">Pour les changements de casse indépendants de la culture, spécifiez `CultureInfo.InvariantCulture` pour le paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="dbdb5-109">Souvent, les chaînes sont converties en casse standard pour faciliter des recherches ultérieures.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="dbdb5-110">Lorsque des chaînes sont utilisées de cette manière, vous devriez spécifier `CultureInfo.InvariantCulture` pour le paramètre `culture`, car la valeur de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> peut changer entre le moment où la casse est modifiée et le moment de la recherche.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="dbdb5-111">Si une décision de sécurité est basée sur une opération de changement de casse, cette opération doit être indépendante de la culture pour garantir que le résultat n'est pas affecté par la valeur de `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="dbdb5-112">Consultez la section « Comparaisons de chaînes qui utilisent la culture actuelle » de l’article [Meilleures pratiques d’utilisation des chaînes](../base-types/best-practices-strings.md) pour voir un exemple montrant comment les opérations de chaînes dépendantes de la culture peuvent produire des résultats incohérents.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="dbdb5-113">Utilisation des méthodes String.ToUpper et String.ToLower</span><span class="sxs-lookup"><span data-stu-id="dbdb5-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="dbdb5-114">Pour la clarté du code, il est recommandé de toujours utiliser des surcharges des méthodes `String.ToUpper` et `String.ToLower` vous permettant de spécifier explicitement un paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="dbdb5-115">Par exemple, le code suivant effectue une recherche d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="dbdb5-116">L’opération `key.ToLower` est dépendante de la culture par défaut, mais ce comportement ne ressort pas clairement de la lecture du code.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="dbdb5-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbdb5-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="dbdb5-118">Si vous souhaitez que l’opération `key.ToLower` soit indépendante de la culture, vous devez modifier l’exemple précédent comme suit pour utiliser explicitement le `CultureInfo.InvariantCulture` lors de la modification de la casse.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="dbdb5-119">Utilisation des méthodes Char.ToUpper et Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="dbdb5-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="dbdb5-120">Bien que les méthodes `Char.ToUpper` et `Char.ToLower` aient les mêmes caractéristiques que les méthodes `String.ToUpper` et `String.ToLower`, les seules cultures affectées sont le turc (Turquie) et l’azéri (latin, Azerbaïdjan).</span><span class="sxs-lookup"><span data-stu-id="dbdb5-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="dbdb5-121">Ce sont les deux seules cultures avec des différences de casse de caractère unique.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="dbdb5-122">Pour plus d’informations sur ce mappage de casse unique, consultez la section « Casse » dans la rubrique de la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="dbdb5-123">Pour la clarté du code et pour garantir des résultats cohérents, il est recommandé de toujours utiliser les surcharges de ces méthodes qui vous permettent de spécifier explicitement un paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="dbdb5-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbdb5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbdb5-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dbdb5-125">Exécution d’opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="dbdb5-125">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
