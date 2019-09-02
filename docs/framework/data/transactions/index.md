---
title: Traitement transactionnel
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: de88247e5916ab6e080c4de361efecee0b193e18
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205907"
---
# <a name="transaction-processing"></a>Traitement transactionnel
Lorsque vous achetez un livre à une librairie en ligne, vous échangez de l'argent (sous forme de crédit) contre ce livre. Si votre crédit est correct, une série d'opérations connexes garantit la réception de votre livre et le versement de l'argent à la librairie. Cependant, si l'une des opérations de la série échoue lors de l'échange, c'est l'échange dans son intégralité qui échoue. Vous ne recevez pas le livre et la librairie ne perçoit pas votre argent.  
  
 La technologie garantissant un échange équilibré et prévisible s'appelle le traitement transactionnel. Les transactions garantissent que les ressources orientées données ne font pas l'objet d'une mise à jour définitive tant que toutes les opérations de l'unité transactionnelle n'ont pas abouti. Grâce à la combinaison d'un jeu d'opérations connexes dans une unité qui a entièrement réussi ou entièrement échoué, vous pouvez simplifier la récupération des erreurs et accroître la fiabilité de votre application.  
  
 Les systèmes de traitement transactionnel sont constitués de matériel et de logiciel informatiques hébergeant une application orientée transaction qui procède aux transactions habituelles nécessaires au traitement des affaires. Les systèmes qui gèrent la saisie de bons de commande, les réservations aériennes, les salaires, les dossiers du personnel, la fabrication et l'expédition en sont des exemples.  
  
 Cette section fournit des informations générales sur le traitement transactionnel et des informations spécifiques sur l'écriture d'applications transactionnelles et de gestionnaires de ressources à l'aide de Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Notions de base des transactions](transaction-fundamentals.md)  
 Présente les concepts et termes de base du traitement transactionnel.  
  
 [Fonctionnalités fournies par System.Transactions](features-provided-by-system-transactions.md)  
 Explique comment utiliser les fonctionnalités de System.Transactions pour écrire votre propre application transactionnelle.  
  
## <a name="reference"></a>Référence  
 <xref:System.Transactions>  
 Fournit les classes qui permettent à votre code de participer à des transactions. Ces classes prennent en charge les transactions présentant plusieurs participants distribués, plusieurs notifications de phase et des inscriptions durables.
