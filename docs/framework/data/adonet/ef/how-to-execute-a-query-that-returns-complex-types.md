---
title: 'Procédure : Exécuter une requête qui retourne des types complexes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 01958637cedcd6d502d51e9f0821ff3a9faae840
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545322"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Procédure : Exécuter une requête qui retourne des types complexes
Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] qui retourne des objets de type d'entité qui contiennent une propriété d'un type complexe.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Double-cliquez sur le fichier. edmx pour afficher le modèle dans la [fenêtre Explorateur de modèles](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) de l’Entity designer. Sur la surface de Entity Designer, sélectionnez `Email` les `Phone` Propriétés et du `Contact` type d’entité, puis cliquez avec le bouton droit et sélectionnez **Refactoriser dans un nouveau type complexe**.  
  
4. Un nouveau type complexe avec les `Email` Propriétés et sélectionnées `Phone` est ajouté à l' **Explorateur de modèles**. Un nom par défaut est attribué au type complexe : renommez le type `EmailPhone` en dans la fenêtre **Propriétés** . Une nouvelle propriété `ComplexProperty` est également ajoutée au type d'entité `Contact`. Renommez la propriété en `EmailPhoneComplexType.`.  
  
     Pour plus d’informations sur la création et la modification de types complexes à l’aide de l’Assistant Entity Data Model, consultez [Comment : Refactoriser des propriétés existantes dans une propriété de type complexe](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) et [Comment : créer et modifier des types complexes](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant exécute une requête qui retourne une collection d' `Contact` objets et affiche deux propriétés des `Contact` objets : `ContactID` et les valeurs du `EmailPhoneComplexType` type complexe.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
