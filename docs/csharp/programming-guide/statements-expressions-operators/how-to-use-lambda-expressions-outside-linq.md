---
title: Activation Utiliser des expressions lambda en dehors de LINQ - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 947f80fdaa90b6b5f8176aac01dd8e3cf40e38cc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363770"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Activation Utiliser des expressions lambda en dehors de LINQ (Guide de programmation C#)
Les expressions lambda ne sont pas limitées aux requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Vous pouvez les utiliser partout où une valeur de délégué est attendue, c’est-à-dire, partout où une méthode anonyme peut être utilisée. L’exemple suivant montre comment utiliser une expression lambda dans un gestionnaire d’événements Windows Forms. Notez que les types des entrées (<xref:System.Object> et <xref:System.Windows.Forms.MouseEventArgs>) sont déduits par le compilateur et n’ont pas à être fournis explicitement dans les paramètres d’entrée lambda.  
  
## <a name="example"></a>Exemples  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [LINQ (Language Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
