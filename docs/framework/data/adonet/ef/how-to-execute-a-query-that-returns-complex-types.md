---
title: 'Procédure : Exécuter une requête qui retourne des types complexes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854640"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Procédure : Exécuter une requête qui retourne des types complexes
Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] qui retourne des objets de type d'entité qui contiennent une propriété d'un type complexe.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Guide pratique pour Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Double-cliquez sur le fichier. edmx pour afficher le modèle dans la [fenêtre Explorateur de modèles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) de l’Entity designer. Sur la surface de Entity designer, sélectionnez `Email` les `Phone` propriétés et du `Contact` type d’entité, puis cliquez avec le bouton droit et sélectionnez **Refactoriser dans un nouveau type complexe**.  
  
4. Un nouveau type complexe avec les propriétés `Email` et `Phone` sélectionnées est ajouté à l' **Explorateur de modèles**. Un nom par défaut est attribué au type complexe : renommez le `EmailPhone` type en dans la fenêtre **Propriétés** . Une nouvelle propriété `ComplexProperty` est également ajoutée au type d'entité `Contact`. Renommez la propriété en `EmailPhoneComplexType.`.  
  
     Pour plus d’informations sur la création et la modification de types complexes à l’aide [de l’Assistant Entity Data Model, consultez Procédure : Refactorisez les propriétés existantes dans une propriété](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) de type complexe et [Comment : Créer et modifier des types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))complexes.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant exécute une requête qui retourne `Contact` une collection d’objets et affiche deux propriétés `Contact` des objets : `ContactID` et les valeurs du `EmailPhoneComplexType` type complexe.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
