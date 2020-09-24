---
title: Fonctions définies par l'utilisateur
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 061e07ba91a1742c90a594bf42f12e64172b2481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164114"
---
# <a name="user-defined-functions"></a><span data-ttu-id="58ac3-102">Fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="58ac3-102">User-Defined Functions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="58ac3-103">utilise des méthodes dans votre modèle objet pour représenter des fonctions définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58ac3-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="58ac3-104">Vous désignez des méthodes comme des fonctions en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58ac3-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="58ac3-105">Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="58ac3-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="58ac3-106">Pour éviter une exception <xref:System.InvalidOperationException>, les fonctions définies par l'utilisateur dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doivent prendre l'une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="58ac3-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="58ac3-107">Fonction encapsulée comme un appel de méthode disposant des attributs de mappage appropriés.</span><span class="sxs-lookup"><span data-stu-id="58ac3-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="58ac3-108">Pour plus d’informations, consultez [mappage basé sur les attributs](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="58ac3-108">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="58ac3-109">Méthode SQL statique spécifique à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58ac3-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="58ac3-110">Fonction prise en charge par une méthode .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58ac3-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="58ac3-111">Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code.</span><span class="sxs-lookup"><span data-stu-id="58ac3-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="58ac3-112">Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel pour mapper des fonctions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58ac3-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58ac3-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="58ac3-113">In This Section</span></span>  

 [<span data-ttu-id="58ac3-114">Procédure : Utiliser des fonctions scalaires définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="58ac3-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="58ac3-115">Décrit comment implémenter une fonction qui retourne des valeurs scalaires.</span><span class="sxs-lookup"><span data-stu-id="58ac3-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="58ac3-116">Procédure : Utiliser des fonctions tables définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="58ac3-116">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="58ac3-117">Décrit comment implémenter une fonction qui retourne des valeurs de table.</span><span class="sxs-lookup"><span data-stu-id="58ac3-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="58ac3-118">Procédure : Appeler des fonctions inline définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="58ac3-118">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="58ac3-119">Décrit comment passer des appels inline à des fonctions et les différences d'exécution lorsque l'appel est rendu inline.</span><span class="sxs-lookup"><span data-stu-id="58ac3-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
