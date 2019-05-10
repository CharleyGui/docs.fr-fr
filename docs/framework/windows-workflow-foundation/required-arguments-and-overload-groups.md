---
title: Arguments obligatoires et groupes surchargés
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: a2a5182adf34c6910f75e85505098075ffe7d3c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649326"
---
# <a name="required-arguments-and-overload-groups"></a>Arguments obligatoires et groupes surchargés
Les activités peuvent être configurées de sorte que certains arguments doivent être liés pour que l'activité soit valide pour l'exécution. L’attribut `RequiredArgument` sert à indiquer que certains arguments sur une activité sont requis et l’attribut `OverloadGroup` à grouper des catégories d’arguments requis. En utilisant les attributs, les auteurs d'activités peuvent fournir des configurations de validation d'activités simples ou complexes.  
  
## <a name="using-required-arguments"></a>Utilisation des arguments requis  
 Pour utiliser l'attribut `RequiredArgument` dans une activité, indiquez les arguments souhaités à l'aide de l'objet <xref:System.Activities.RequiredArgumentAttribute>. Cet exemple consiste à définir une activité `Add` qui a deux arguments requis.  
  
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
  
 En XAML, les arguments requis sont également indiqués à l'aide de l'objet <xref:System.Activities.RequiredArgumentAttribute>. Dans cet exemple, l'activité `Add` est définie à l'aide de trois arguments et utilise une activité <xref:System.Activities.Statements.Assign%601> pour effectuer l'opération d'ajout.  
  
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
  
 Si l'activité est utilisée et l'un ou l'autre des arguments requis n'est pas lié, l'erreur de validation suivante est retournée :  
  
 **Valeur pour un argument d’activité 'operand1 ' requis n’a pas été fournie.**  
> [!NOTE]
> Pour plus d’informations sur la vérification et gestion des erreurs de validation et avertissements, consultez [appel de Validation d’activité](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Utilisation des groupes surchargés

Les groupes surchargés fournissent une méthode permettant d’indiquer quelles combinaisons d’arguments sont valides dans une activité. Les arguments sont groupés à l'aide de l'objet <xref:System.Activities.OverloadGroupAttribute>. Chaque groupe porte un nom spécifié par le <xref:System.Activities.OverloadGroupAttribute>. L’activité est valide lorsque qu’un seul jeu d’arguments dans un groupe surchargé sont liés. Dans l'exemple suivant, une classe `CreateLocation` est définie.  
  
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
  
 L'objectif de cette activité est de spécifier un emplacement aux États-Unis d'Amérique. Pour ce faire, l'utilisateur de l'activité peut spécifier l'emplacement à l'aide de l'un des trois groupes d'arguments. Pour spécifier les combinaisons valides des arguments, trois groupes surchargés sont définis. `G1` contient les arguments `Latitude` et `Longitude`. `G2` contient `Street`, `City` et `State`. `G3` contient `Street` et `Zip`. `Name` est également un argument obligatoire, mais il ne fait pas partie d'un groupe surchargé. Pour que cette activité soit valide, `Name` devrait être lié, ainsi que tous les arguments d'un seul et unique groupe surchargé.  
  
 Dans l’exemple suivant, extrait de la [activités d’accès de base de données](./samples/database-access-activities.md) exemple, il existe deux groupes surchargés : `ConnectionString` et `ConfigFileSectionName`. Pour que cette activité soit valide, les arguments `ProviderName` et `ConnectionString` doivent être liés, ou l’argument `ConfigName`, mais pas les deux.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
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
  
 Lors de la définition d'un groupe surchargé :  
  
- Un groupe surchargé ne peut pas être un sous-ensemble ou un ensemble équivalent d'un autre groupe surchargé.  
  
    > [!NOTE]
    >  Il existe une exception à cette règle. Si un groupe surchargé est un sous-ensemble d’un autre groupe surchargé, et le sous-ensemble contient uniquement des arguments où `RequiredArgument` a la valeur `false`, le groupe surchargé est valide.  
  
- Les groupes surchargés peuvent se chevaucher, mais il se produit une erreur si l’intersection des groupes contient tous les arguments obligatoires d’un groupe surchargé ou des deux. Dans l’exemple précédent les groupes surchargés `G2` et `G3` se chevauchaient, mais comme l’intersection ne contenait pas tous les arguments d’un ou des deux groupes, elle était valide.  
  
 Lors de la liaison des arguments dans un groupe surchargé :  
  
- Un groupe surchargé est considéré comme lié si tous les arguments `RequiredArgument` de celui-ci sont liés.  
  
- Si un groupe n’a aucun argument `RequiredArgument` et au moins un argument lié, il est considéré comme lié.  
  
- Si aucun des groupes surchargés n'est lié à moins qu'un groupe surchargé ne contienne aucun argument `RequiredArgument`, cela correspond à une erreur.  
  
- Il se produit une erreur si vous avez plusieurs groupes surchargés liés, autrement dit si tous les arguments obligatoires d'un groupe surchargé sont liés et qu'un argument d'un autre groupe surchargé est également lié.
