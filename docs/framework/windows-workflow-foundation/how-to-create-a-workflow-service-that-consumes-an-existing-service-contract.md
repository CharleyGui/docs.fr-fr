---
title: 'Procédure : créer un service de workflow qui consomme un contrat de service existant'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248823"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Procédure : créer un service de workflow qui consomme un contrat de service existant

.NET Framework 4,5 offre une meilleure intégration entre les services Web et les workflows sous la forme d’un développement de workflow contrat en premier. L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier. L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat.  
  
> [!NOTE]
> Cette rubrique fournit des instructions pas à pas pour créer un service de workflow contrat en premier. Pour plus d’informations sur le développement d’un service de workflow contrat en premier, consultez développement d’un [service de flux de travail en premier contrat](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Création du projet de workflow  
  
1. Dans Visual Studio, sélectionnez **Fichier**, **Nouveau projet**. Sélectionnez le nœud **WCF** sous le nœud **C#** dans l’arborescence **modèles** , puis sélectionnez le modèle application de service de flux de **travail WCF** .  
  
2. Nommez le nouveau projet `ContractFirst` , puis cliquez sur **OK**.  
  
### <a name="creating-the-service-contract"></a>Création du contrat de service  
  
1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **nouvel élément...**. Sélectionnez le nœud **code** sur la gauche, et le modèle de **classe** à droite. Nommez la nouvelle classe `IBookService` , puis cliquez sur **OK**.  
  
2. En haut de la fenêtre de code qui apparaît, ajoutez une instruction Using à `System.Servicemodel`.  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. Remplacez la définition d'exemple de classe par la définition d'interface suivante.  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. Générez le projet en appuyant sur **Ctrl + Maj + B**.  
  
### <a name="importing-the-service-contract"></a>Importation du contrat de service  
  
1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **importer le contrat de service**. Sous **\<Current Project>** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**. Cliquez sur **OK**.  
  
2. Une boîte de dialogue s'ouvre indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées s'afficheront dans la boîte à outils une fois le projet construit. Cliquez sur **OK**.  
  
3. Générez le projet en appuyant sur **Ctrl + Maj + B**, afin que les activités importées s’affichent dans la boîte à outils.  
  
4. Dans **Explorateur de solutions**, ouvrez Service1. xamlx. Le service de workflow apparaît dans le concepteur.  
  
5. Sélectionnez l’activité **séquence** . Dans le Fenêtre Propriétés, cliquez sur **...** dans la propriété **ImplementedContract** . Dans la fenêtre de l' **éditeur de collections type** qui s’affiche, cliquez sur la liste déroulante **type** , puis sélectionnez **Rechercher des types...** mention. Dans la boîte de dialogue **Rechercher et sélectionner un type .net** , sous **\<Current Project>** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**. Cliquez sur **OK**. Dans la boîte de dialogue **éditeur de collections de types** , cliquez sur **OK**.  
  
6. Sélectionnez et supprimez les activités **ReceiveRequest** et **SendResponse** .  
  
7. À partir de la boîte à outils, faites glisser un **Buy_ReceiveAndSendReply** et une activité de **Checkout_Receive** sur l’activité de **service séquentielle** .
