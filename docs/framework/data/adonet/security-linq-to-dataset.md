---
title: Sécurité (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504256"
---
# <a name="security-linq-to-dataset"></a>Sécurité (LINQ to DataSet)
Cette rubrique décrit les problèmes de sécurité dans LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Passage d'une requête à un composant non approuvé  
 Une requête LINQ to DataSet peut être formulée à un point d’un programme et exécutée dans une autre. Au point précis où elle est formulée, la requête peut référencer tout élément qui y est visible, comme des membres privés de la classe à laquelle appartient la méthode appelante, ou des symboles représentant les variables/arguments locaux. Au moment de l'exécution, la requête pourra accéder aux membres qu'elle a référencés au moment de la formulation, même si le code appelant ne les voit pas. Le code qui exécute la requête ne peut avoir aucune visibilité arbitraire du fait qu'il ne peut pas choisir les éléments auxquels il peut accéder. Il accède strictement aux mêmes éléments que la requête, et uniquement à travers la requête.  
  
 Pour cela, il faut qu'en passant une référence à une requête à une autre partie du code, le composant recevant la requête soit approuvé auprès de tous les membres publics et privés auxquels la requête fait référence. En règle générale, les requêtes LINQ to DataSet ne doit pas être passé aux composants non approuvés, à moins que la requête a été construite avec soin afin qu’elle n’expose pas les informations devant rester confidentielles.  
  
## <a name="external-input"></a>Entrée externe  
 Les applications reçoivent souvent des entrées externes (provenant d'un utilisateur ou d'un autre agent externe) et exécutent des actions en fonction de ces entrées.  Dans le cas de LINQ to DataSet, l’application peut construire une requête d’une certaine manière, en fonction de l’entrée externe ou utiliser une entrée dans la requête externe. Requêtes LINQ to DataSet acceptent des paramètres partout où des littéraux sont admis. Les développeurs d'applications devraient utiliser des requêtes paramétrées, plutôt que d'injecter des littéraux directement dans la requête à partir d'un agent externe.  
  
 Toute entrée provenant directement ou indirectement d'un utilisateur ou d'un agent externe doit avoir un contenu qui se base sur la syntaxe du langage cible afin d'exécuter des actions non autorisées. C'est ce que l'on appelle une « attaque par injection de code SQL », terme dérivé d'un modèle d'attaque où le langage cible est Transact-SQL. L’entrée utilisateur injectée directement dans la requête est utilisée pour effacer une table de base de données, provoquer un déni de service, ou modifier d’une manière ou d’une autre la nature de l’opération en cours. Bien que la composition de requête n’est possible dans LINQ to DataSet, elle est effectuée via l’API de modèle objet. Requêtes LINQ to DataSet ne sont pas composées par manipulation ou concaténation, tels qu’ils se trouvent dans Transact-SQL, ne sont pas vulnérables aux attaques d’injection SQL dans le sens traditionnel.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
