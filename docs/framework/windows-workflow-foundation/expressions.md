---
title: Expressions - WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93fe449e8fa6c50f715d842c2ef6a9ecbd31aff2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182940"
---
# <a name="expressions"></a>Expressions

Une expression de la Windows Workflow Foundation (WF) est toute activité qui renvoie un résultat. Toutes les activités d'expression dérivent indirectement de <xref:System.Activities.Activity%601>, qui contient une propriété <xref:System.Activities.OutArgument> nommée <xref:System.Activities.Activity%601.Result%2A> comme valeur de retour de l'activité. [!INCLUDE[wf1](../../../includes/wf1-md.md)] est fourni avec une large gamme d'activités d'expressions, simples comme <xref:System.Activities.Expressions.VariableValue%601> et <xref:System.Activities.Expressions.VariableReference%601>, qui permettent d'accéder à une variable de workflow unique via des activités d'opérateur, ou complexes telles que <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> et <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> qui permettent d'accéder à la totalité du langage Visual Basic pour produire le résultat. Des activités d'expressions supplémentaires peuvent être créées en dérivant de <xref:System.Activities.CodeActivity%601> ou <xref:System.Activities.NativeActivity%601>.

## <a name="using-expressions"></a>Utilisation d'expressions
 Le concepteur de workflow utilise <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> et <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pour les expressions dans les projets Visual Basic, et <xref:Microsoft.CSharp.Activities.CSharpValue%601> et <xref:Microsoft.CSharp.Activities.CSharpReference%601> pour les expressions dans les projets de workflow C#.

> [!NOTE]
> Le soutien aux expressions de C dans les projets de flux de travail a été introduit dans le cadre .NET 4.5. Pour plus d’informations, voir [expressions de C .](csharp-expressions.md)

 Les workflows produits par le concepteur sont enregistrés en XAML, où les expressions s'affichent entre crochets, comme dans l'exemple suivant.

```xml
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <Sequence.Variables>
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />
  </Sequence.Variables>
  <Assign>
    <Assign.To>
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>
    </Assign.To>
    <Assign.Value>
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>
    </Assign.Value>
  </Assign>
</Sequence>
```

 Lors de la définition d'un workflow dans le code, toutes les activités d'expressions peuvent être utilisées. L’exemple suivant montre l’utilisation d’une composition des activités de l’opérateur pour ajouter trois numéros :

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new Add<int, int, int> {
                    Left = new Add<int, int, int> {
                        Left = new InArgument<int>(a),
                        Right = new InArgument<int>(b)
                    },
                    Right = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Le même flux de travail peut être exprimé plus compactement en utilisant des expressions de lambda de C, comme le montre l’exemple suivant :
  
```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))
        }
    }
};
```

## <a name="extending-available-expressions-with-custom-expression-activities"></a>Extension d'expressions disponibles avec les activités d'expressions personnalisées

 Les expressions dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sont extensibles, ce qui permet la création d'activités d'expressions supplémentaires. L'exemple suivant affiche une activité qui retourne une somme de trois valeurs entières.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Activities;

namespace ExpressionsDemo
{
    public sealed class AddThreeValues : CodeActivity<int>
    {
        public InArgument<int> Value1 { get; set; }
        public InArgument<int> Value2 { get; set; }
        public InArgument<int> Value3 { get; set; }

        protected override int Execute(CodeActivityContext context)
        {
            return Value1.Get(context) +
                   Value2.Get(context) +
                   Value3.Get(context);
        }
    }
}
```

 Avec cette nouvelle activité, vous pouvez réécrire le flux de travail précédent qui a ajouté trois valeurs comme indiqué dans l’exemple suivant:

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new AddThreeValues() {
                    Value1 = new InArgument<int>(a),
                    Value2 = new InArgument<int>(b),
                    Value3 = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Pour plus d’informations sur l’utilisation des expressions dans le code, voir [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).
