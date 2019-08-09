---
title: Expressions-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 092272db2f7979cf12917dfe35e116295db79bf3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868895"
---
# <a name="expressions"></a><span data-ttu-id="766da-102">Expressions</span><span class="sxs-lookup"><span data-stu-id="766da-102">Expressions</span></span>
<span data-ttu-id="766da-103">Une expression Windows Workflow Foundation (WF) est toute activité qui retourne un résultat.</span><span class="sxs-lookup"><span data-stu-id="766da-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="766da-104">Toutes les activités d'expression dérivent indirectement de <xref:System.Activities.Activity%601>, qui contient une propriété <xref:System.Activities.OutArgument> nommée <xref:System.Activities.Activity%601.Result%2A> comme valeur de retour de l'activité.</span><span class="sxs-lookup"><span data-stu-id="766da-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="766da-105">est fourni avec une large gamme d'activités d'expressions, simples comme <xref:System.Activities.Expressions.VariableValue%601> et <xref:System.Activities.Expressions.VariableReference%601>, qui permettent d'accéder à une variable de workflow unique via des activités d'opérateur, ou complexes telles que <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> et <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> qui permettent d'accéder à la totalité du langage Visual Basic pour produire le résultat.</span><span class="sxs-lookup"><span data-stu-id="766da-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="766da-106">Des activités d'expressions supplémentaires peuvent être créées en dérivant de <xref:System.Activities.CodeActivity%601> ou <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="766da-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="766da-107">Utilisation d'expressions</span><span class="sxs-lookup"><span data-stu-id="766da-107">Using Expressions</span></span>  
 <span data-ttu-id="766da-108">Le concepteur de workflow utilise <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> et <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pour les expressions dans les projets Visual Basic, et <xref:Microsoft.CSharp.Activities.CSharpValue%601> et <xref:Microsoft.CSharp.Activities.CSharpReference%601> pour les expressions dans les projets de workflow C#.</span><span class="sxs-lookup"><span data-stu-id="766da-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="766da-109">La prise C# en charge des expressions dans les projets de workflow a été introduite dans .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="766da-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="766da-110">Pour plus d’informations, consultez [ C# expressions](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="766da-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="766da-111">Les workflows produits par le concepteur sont enregistrés en XAML, où les expressions s'affichent entre crochets, comme dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="766da-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="766da-112">Lors de la définition d'un workflow dans le code, toutes les activités d'expressions peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="766da-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="766da-113">L'exemple suivant illustre l'utilisation d'une composition d'activités d'opérateur pour ajouter trois nombres.</span><span class="sxs-lookup"><span data-stu-id="766da-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
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
  
 <span data-ttu-id="766da-114">Le même workflow peut être exprimé d’une manière plus compacte en utilisant des expressions lambda C#, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="766da-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="766da-115">Le workflow peut également être exprimé à l'aide des activités d'expressions Visual Basic, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="766da-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
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
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="766da-116">Extension d'expressions disponibles avec les activités d'expressions personnalisées</span><span class="sxs-lookup"><span data-stu-id="766da-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="766da-117">Les expressions dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sont extensibles, ce qui permet la création d'activités d'expressions supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="766da-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="766da-118">L'exemple suivant affiche une activité qui retourne une somme de trois valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="766da-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
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
  
 <span data-ttu-id="766da-119">Avec cette nouvelle activité, vous pouvez réécrire le workflow précédent qui a ajouté trois valeurs comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="766da-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="766da-120">Pour plus d’informations sur l’utilisation d’expressions dans le code, consultez [création de flux de travail, d’activités et d’expressions à l’aide du code impératif](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="766da-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
