---
title: Procédures stockées
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 57420d95ec27af3b572940202fb6bc288c6888da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203512"
---
# <a name="stored-procedures"></a>Procédures stockées

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des méthodes dans votre modèle objet pour représenter des procédures stockées dans la base de données. Vous désignez des méthodes comme des procédures stockées en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>. Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).  
  
 Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel pour mapper des procédures stockées. Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Procédure : Retourner des ensembles de lignes](how-to-return-rowsets.md)  
 Décrit comment retourner des lignes de données et comment utiliser un paramètre d'entrée.  
  
 [Procédure : Utiliser des procédures stockées qui prennent des paramètres](how-to-use-stored-procedures-that-take-parameters.md)  
 Décrit comment utiliser des paramètres d'entrée et de sortie.  
  
 [Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 Explique comment permettre le retour de plusieurs formes dans la même procédure stockée.  
  
 [Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 Explique comment permettre plusieurs formes lorsque la séquence de retour est connue.  
  
 [Personnalisation d'opérations à l'aide de procédures stockées](customizing-operations-by-using-stored-procedures.md)  
 Explique comment utiliser des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.  
  
 [Personnalisation d'opérations à l'aide de procédures stockées uniquement](customizing-operations-by-using-stored-procedures-exclusively.md)  
 Explique comment utiliser uniquement des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.  
  
## <a name="related-sections"></a>Sections connexes  

 [Guide de programmation](programming-guide.md)  
 Fournit des informations sur la création et l'utilisation de votre modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Procédure pas à pas : Utilisation de procédures stockées uniquement (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)  
 Inclut des procédures qui expliquent comment utiliser des procédures stockées dans Visual Basic.  
  
 [Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)](walkthrough-using-only-stored-procedures-csharp.md)  
 Inclut des procédures qui expliquent comment utiliser des procédures stockées dans C#.
