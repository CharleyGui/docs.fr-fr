---
title: 'Procédure : recevoir des notifications des exceptions de première chance'
description: Obtenir des notifications d’exceptions de première chance dans .NET via l’événement FirstChanceException de la classe AppDomain, avant que le CLR ne recherche des gestionnaires d’exceptions.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
ms.openlocfilehash: 0b3150a52a68e078d1052a9894bb652ad35027d0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242563"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Procédure : recevoir des notifications des exceptions de première chance

L’événement <xref:System.AppDomain.FirstChanceException> de la classe <xref:System.AppDomain> vous permet de recevoir la notification qu’une exception a été levée, avant que le Common Language Runtime n’ait commencé à rechercher des gestionnaires d’exceptions.

 L’événement est déclenché au niveau du domaine d’application. Étant donné qu’un thread d’exécution peut traverser plusieurs domaines d’application, une exception qui n’est pas gérée dans un domaine d’application pourrait être gérée dans un autre domaine d’application. La notification se produit dans chaque domaine d’application qui a ajouté un gestionnaire pour l’événement, jusqu’à ce qu’un domaine d’application gère l’exception.

 Les procédures et exemples dans cet article indiquent comment recevoir des notifications des exceptions de première chance dans un programme simple qui a un domaine d’application, et dans un domaine d’application que vous créez.

 Pour obtenir un exemple plus complexe qui couvre plusieurs domaines d’application, consultez l’exemple de l’événement <xref:System.AppDomain.FirstChanceException>.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Réception de notifications des exceptions de première chance dans le domaine d’application par défaut

 Dans la procédure suivante, le point d’entrée de l’application (la méthode `Main()`) s’exécute dans le domaine d’application par défaut.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Pour illustrer les notifications des exceptions de première chance dans le domaine d’application par défaut

1. Définissez un gestionnaire d’événements pour l’événement <xref:System.AppDomain.FirstChanceException>, à l’aide d’une fonction lambda, et attachez-le à l’événement. Dans cet exemple, le gestionnaire d’événements imprime le nom du domaine d’application où l’événement a été géré, ainsi que la propriété <xref:System.Exception.Message%2A> de l’exception.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. Levez une exception et interceptez-la. Avant que le runtime ne trouve le gestionnaire d’exceptions, l’événement <xref:System.AppDomain.FirstChanceException> est déclenché et affiche un message. Ce message est suivi du message affiché par le gestionnaire d’exceptions.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. Levez une exception mais ne l’interceptez pas. Avant que le runtime ne recherche le gestionnaire d’exceptions, l’événement <xref:System.AppDomain.FirstChanceException> est déclenché et affiche un message. Comme il n’y a aucun gestionnaire d’exceptions, l’application s’arrête.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Le code affiché aux trois premières étapes de cette procédure forme une application console complète. La sortie de l’application varie en fonction du nom du fichier .exe, car le nom du domaine d’application par défaut se compose du nom et de l’extension du fichier .exe. Vous trouverez ci-dessous un exemple de sortie.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Réception de notifications des exceptions de première chance dans un autre domaine d’application

 Si votre programme contient plusieurs domaines d’application, vous pouvez choisir ceux qui reçoivent des notifications.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Pour recevoir des notifications des exceptions de première chance dans un domaine d’application que vous créez

1. Définissez un gestionnaire d’événements pour l’événement <xref:System.AppDomain.FirstChanceException>. Cet exemple utilise une méthode `static` (méthode `Shared` en Visual Basic) qui imprime le nom du domaine d’application où l’événement a été géré, ainsi que la propriété <xref:System.Exception.Message%2A> de l’exception.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. Créez un domaine d’application et ajoutez le gestionnaire d’événements à l’événement <xref:System.AppDomain.FirstChanceException> pour ce domaine d’application. Dans cet exemple, le domaine d’application se nomme `AD1`.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     Vous pouvez gérer cet événement dans le domaine d’application par défaut de la même façon. Utilisez la propriété `static` (`Shared` en Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> dans `Main()` pour obtenir une référence au domaine d’application par défaut.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Pour illustrer les notifications des exceptions de première chance dans le domaine d’application

1. Créez un objet `Worker` dans le domaine d’application que vous avez créé lors de la procédure précédente. La classe `Worker` doit être publique et doit dériver de <xref:System.MarshalByRefObject>, comme indiqué dans l’exemple complet à la fin de cet article.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. Appelez une méthode de l’objet `Worker` qui lève une exception. Dans cet exemple, la méthode `Thrower` est appelée deux fois. La première fois, l’argument de méthode est `true`. La méthode intercepte donc sa propre exception. La deuxième fois, l’argument est `false`, et la méthode `Main()` intercepte l’exception dans le domaine d’application par défaut.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. Placez le code dans la méthode `Thrower` pour contrôler si la méthode gère sa propre exception.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a> Exemple

 L’exemple suivant crée un domaine d’application nommé `AD1` et ajoute un gestionnaire d’événements à l’événement <xref:System.AppDomain.FirstChanceException> du domaine d’application. L’exemple crée une instance de la classe `Worker` dans le domaine d’application et appelle une méthode nommée `Thrower` qui lève une <xref:System.ArgumentException>. En fonction de la valeur de son argument, la méthode intercepte l’exception ou ne parvient pas à la gérer.

 Chaque fois que la méthode `Thrower` lève une exception dans `AD1`, l’événement <xref:System.AppDomain.FirstChanceException> est déclenché dans `AD1`, et le gestionnaire d’événements affiche un message. Le runtime recherche ensuite un gestionnaire d’exceptions. Dans le premier cas, le gestionnaire d’exceptions est trouvé dans `AD1`. Dans le deuxième cas, l’exception n’est pas gérée dans `AD1` ; elle est interceptée dans le domaine d’application par défaut.

> [!NOTE]
> Le nom du domaine d’application par défaut est identique au nom de l’exécutable.

 Si vous ajoutez un gestionnaire pour l’événement <xref:System.AppDomain.FirstChanceException> au domaine d’application par défaut, l’événement est déclenché et géré avant que le domaine d’application par défaut ne gère l’exception. Pour afficher cela, ajoutez le code C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (en Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) au début de `Main()`.

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain.FirstChanceException>
