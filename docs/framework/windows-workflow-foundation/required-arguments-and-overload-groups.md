---
title: Arguments obligatoires et groupes surchargés
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 452285b1f5b73ecf75fc50f59365aa2633f26e42
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245872"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="a1a92-102">Arguments obligatoires et groupes surchargés</span><span class="sxs-lookup"><span data-stu-id="a1a92-102">Required Arguments and Overload Groups</span></span>

<span data-ttu-id="a1a92-103">Les activités peuvent être configurées de sorte que certains arguments doivent être liés pour que l'activité soit valide pour l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a1a92-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="a1a92-104">L’attribut `RequiredArgument` sert à indiquer que certains arguments sur une activité sont requis et l’attribut `OverloadGroup` à grouper des catégories d’arguments requis.</span><span class="sxs-lookup"><span data-stu-id="a1a92-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="a1a92-105">En utilisant les attributs, les auteurs d'activités peuvent fournir des configurations de validation d'activités simples ou complexes.</span><span class="sxs-lookup"><span data-stu-id="a1a92-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="a1a92-106">Utilisation des arguments requis</span><span class="sxs-lookup"><span data-stu-id="a1a92-106">Using Required Arguments</span></span>  

 <span data-ttu-id="a1a92-107">Pour utiliser l'attribut `RequiredArgument` dans une activité, indiquez les arguments souhaités à l'aide de l'objet <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a1a92-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="a1a92-108">Cet exemple consiste à définir une activité `Add` qui a deux arguments requis.</span><span class="sxs-lookup"><span data-stu-id="a1a92-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="a1a92-109">En XAML, les arguments requis sont également indiqués à l'aide de l'objet <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a1a92-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="a1a92-110">Dans cet exemple, l'activité `Add` est définie à l'aide de trois arguments et utilise une activité <xref:System.Activities.Statements.Assign%601> pour effectuer l'opération d'ajout.</span><span class="sxs-lookup"><span data-stu-id="a1a92-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="a1a92-111">Si l'activité est utilisée et l'un ou l'autre des arguments requis n'est pas lié, l'erreur de validation suivante est retournée :</span><span class="sxs-lookup"><span data-stu-id="a1a92-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="a1a92-112">**La valeur « Operand1 » d’un argument requis d’activité n’a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="a1a92-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="a1a92-113">Pour plus d’informations sur la vérification et la gestion des erreurs et des avertissements de validation, consultez [appel de validation d’activité](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="a1a92-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="a1a92-114">Utilisation des groupes surchargés</span><span class="sxs-lookup"><span data-stu-id="a1a92-114">Using Overload Groups</span></span>

<span data-ttu-id="a1a92-115">Les groupes surchargés fournissent une méthode permettant d’indiquer quelles combinaisons d’arguments sont valides dans une activité.</span><span class="sxs-lookup"><span data-stu-id="a1a92-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="a1a92-116">Les arguments sont groupés à l'aide de l'objet <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a1a92-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="a1a92-117">Un nom spécifié par le est attribué à chaque groupe <xref:System.Activities.OverloadGroupAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a1a92-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="a1a92-118">L’activité est valide lorsqu’un seul jeu d’arguments dans un groupe surchargé est lié.</span><span class="sxs-lookup"><span data-stu-id="a1a92-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="a1a92-119">Dans l'exemple suivant, une classe `CreateLocation` est définie.</span><span class="sxs-lookup"><span data-stu-id="a1a92-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }
}  
```  
  
 <span data-ttu-id="a1a92-120">L'objectif de cette activité est de spécifier un emplacement aux États-Unis d'Amérique.</span><span class="sxs-lookup"><span data-stu-id="a1a92-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="a1a92-121">Pour ce faire, l'utilisateur de l'activité peut spécifier l'emplacement à l'aide de l'un des trois groupes d'arguments.</span><span class="sxs-lookup"><span data-stu-id="a1a92-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="a1a92-122">Pour spécifier les combinaisons valides des arguments, trois groupes surchargés sont définis.</span><span class="sxs-lookup"><span data-stu-id="a1a92-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="a1a92-123">`G1` contient les arguments `Latitude` et `Longitude`.</span><span class="sxs-lookup"><span data-stu-id="a1a92-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="a1a92-124">`G2` contient `Street`, `City` et `State`.</span><span class="sxs-lookup"><span data-stu-id="a1a92-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="a1a92-125">`G3` contient `Street` et `Zip`.</span><span class="sxs-lookup"><span data-stu-id="a1a92-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="a1a92-126">`Name` est également un argument obligatoire, mais il ne fait pas partie d'un groupe surchargé.</span><span class="sxs-lookup"><span data-stu-id="a1a92-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="a1a92-127">Pour que cette activité soit valide, `Name` devrait être lié, ainsi que tous les arguments d'un seul et unique groupe surchargé.</span><span class="sxs-lookup"><span data-stu-id="a1a92-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="a1a92-128">Dans l’exemple suivant, extrait de l’exemple d’activités d’accès à la [base de données](./samples/database-access-activities.md) , il existe deux groupes surchargés : `ConnectionString` et `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="a1a92-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="a1a92-129">Pour que cette activité soit valide, les arguments `ProviderName` et `ConnectionString` doivent être liés, ou l’argument `ConfigName`, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="a1a92-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }
}  
```  
  
 <span data-ttu-id="a1a92-130">Lors de la définition d'un groupe surchargé :</span><span class="sxs-lookup"><span data-stu-id="a1a92-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="a1a92-131">Un groupe surchargé ne peut pas être un sous-ensemble ou un ensemble équivalent d'un autre groupe surchargé.</span><span class="sxs-lookup"><span data-stu-id="a1a92-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1a92-132">Il existe une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="a1a92-132">There is one exception to this rule.</span></span> <span data-ttu-id="a1a92-133">Si un groupe surchargé est un sous-ensemble d’un autre groupe surchargé, et le sous-ensemble contient uniquement des arguments où `RequiredArgument` a la valeur `false`, le groupe surchargé est valide.</span><span class="sxs-lookup"><span data-stu-id="a1a92-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="a1a92-134">Les groupes surchargés peuvent se chevaucher, mais il se produit une erreur si l’intersection des groupes contient tous les arguments obligatoires d’un groupe surchargé ou des deux.</span><span class="sxs-lookup"><span data-stu-id="a1a92-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="a1a92-135">Dans l’exemple précédent les groupes surchargés `G2` et `G3` se chevauchaient, mais comme l’intersection ne contenait pas tous les arguments d’un ou des deux groupes, elle était valide.</span><span class="sxs-lookup"><span data-stu-id="a1a92-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="a1a92-136">Lors de la liaison des arguments dans un groupe surchargé :</span><span class="sxs-lookup"><span data-stu-id="a1a92-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="a1a92-137">Un groupe surchargé est considéré comme lié si tous les arguments `RequiredArgument` de celui-ci sont liés.</span><span class="sxs-lookup"><span data-stu-id="a1a92-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="a1a92-138">Si un groupe n’a aucun argument `RequiredArgument` et au moins un argument lié, il est considéré comme lié.</span><span class="sxs-lookup"><span data-stu-id="a1a92-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="a1a92-139">Si aucun des groupes surchargés n'est lié à moins qu'un groupe surchargé ne contienne aucun argument `RequiredArgument`, cela correspond à une erreur.</span><span class="sxs-lookup"><span data-stu-id="a1a92-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="a1a92-140">Il se produit une erreur si vous avez plusieurs groupes surchargés liés, autrement dit si tous les arguments obligatoires d'un groupe surchargé sont liés et qu'un argument d'un autre groupe surchargé est également lié.</span><span class="sxs-lookup"><span data-stu-id="a1a92-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
