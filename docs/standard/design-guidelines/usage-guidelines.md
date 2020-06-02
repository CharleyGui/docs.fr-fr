---
title: Indications relatives à l'utilisation
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291342"
---
# <a name="usage-guidelines"></a><span data-ttu-id="e21ba-102">Indications relatives à l'utilisation</span><span class="sxs-lookup"><span data-stu-id="e21ba-102">Usage guidelines</span></span>

<span data-ttu-id="e21ba-103">Cette section contient des instructions pour l’utilisation des types courants dans les API accessibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="e21ba-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="e21ba-104">Il traite de l’utilisation directe des types d’infrastructure intégrés (par exemple, les attributs de sérialisation) et de la surcharge des opérateurs courants.</span><span class="sxs-lookup"><span data-stu-id="e21ba-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="e21ba-105">L' <xref:System.IDisposable?displayProperty=nameWithType> interface n’est pas traitée dans cette section, mais elle est décrite dans la section [modèle de suppression](../garbage-collection/implementing-dispose.md) .</span><span class="sxs-lookup"><span data-stu-id="e21ba-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="e21ba-106">Pour obtenir des instructions et des informations supplémentaires sur d’autres types de .NET Framework intégrés communs, consultez les rubriques de référence pour les éléments suivants : <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> , <xref:System.ICloneable?displayProperty=nameWithType> , <xref:System.IComparable%601?displayProperty=nameWithType> , <xref:System.IEquatable%601?displayProperty=nameWithType> , <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e21ba-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e21ba-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e21ba-107">In this section</span></span>

[<span data-ttu-id="e21ba-108">Tableaux</span><span class="sxs-lookup"><span data-stu-id="e21ba-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="e21ba-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e21ba-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="e21ba-110">Regroupements</span><span class="sxs-lookup"><span data-stu-id="e21ba-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="e21ba-111">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e21ba-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="e21ba-112">Utilisation de System. Xml</span><span class="sxs-lookup"><span data-stu-id="e21ba-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="e21ba-113">Opérateurs d’égalité</span><span class="sxs-lookup"><span data-stu-id="e21ba-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="e21ba-114">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="e21ba-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="e21ba-115">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e21ba-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e21ba-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e21ba-116">See also</span></span>

- [<span data-ttu-id="e21ba-117">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="e21ba-117">Framework Design Guidelines</span></span>](index.md)
