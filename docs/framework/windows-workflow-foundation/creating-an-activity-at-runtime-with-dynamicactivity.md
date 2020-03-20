---
title: Création d'une activité en cours d'exécution avec DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182990"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Création d'une activité en cours d'exécution avec DynamicActivity
<xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public. <xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.  
  
## <a name="dynamicactivity-features"></a>Fonctionnalités DynamicActivity  
 L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.  
  
 Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail. En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type. En XAML, ils sont déclarés à l’aide d’étiquettes `x:Class` et `x:Member`.  
  
 Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>. Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Pour créer une activité au moment de l'exécution à l'aide du code impératif  
  
1. Studio OpenVisual 2010.  
  
2. Sélectionnez **Fichier**, **Nouveau**, **Projet**. Sélectionnez **Workflow 4.0** sous **Visual CMD** dans la fenêtre **Project Types** et sélectionnez le nœud **v2010.** Sélectionnez **l’application de console de flux de travail séquentielle** dans la fenêtre **Templates.** Nommez le nouveau projet « DynamicActivitySample ».  
  
3. Cliquez à droite Workflow1.xaml dans le projet HelloActivity et **sélectionnez Supprimer**.  
  
4. Ouvrez le fichier Program.cs. Ajoutez la directive suivante en début de fichier.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Remplacez le contenu de la méthode `Main` par le code ci-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. Exécutez l'application. Une fenêtre console avec le texte "Bonjour monde!" Affiche.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Pour créer une activité au moment de l'exécution à l'aide de XAML  
  
1. Open Visual Studio 2010.  
  
2. Sélectionnez **Fichier**, **Nouveau**, **Projet**. Sélectionnez **Workflow 4.0** sous **Visual CMD** dans la fenêtre **Project Types** et sélectionnez le nœud **v2010.** Sélectionnez **l’application de console workflow** dans la fenêtre **Templates.** Nommez le nouveau projet « DynamicActivitySample ».  
  
3. Dans le projet HelloActivity, ouvrez Workflow1.xaml. Cliquez sur l’option **Arguments** au bas du designer. Créez un argument `In` appelé `TextToWrite` de type `String`.  
  
4. Faites glisser une activité **WriteLine** de la section **Primitives** de la boîte à outils sur la surface du concepteur. Attribuer la `TextToWrite` valeur à la propriété **Text** de l’activité.  
  
5. Ouvrez le fichier Program.cs. Ajoutez la directive suivante en début de fichier.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Remplacez le contenu de la méthode `Main` par le code suivant :  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Exécutez l'application. Une fenêtre console avec le texte "Bonjour monde!"  s’affiche.  
  
8. Cliquez à droite sur le fichier Workflow1.xaml dans le **Solution Explorer** et sélectionnez **Le code de vue**. Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.  
  
## <a name="see-also"></a>Voir aussi

- [Création de workflows, d’activités et d’expressions à l’aide du code impératif](authoring-workflows-activities-and-expressions-using-imperative-code.md)
