---
title: Mises à niveau de flux personnalisées
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 3ef0f59a5d63c24188b29cb7a38db2d6323d80ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295576"
---
# <a name="custom-stream-upgrades"></a>Mises à niveau de flux personnalisées

Les transports orientés flux, tels que TCP et Canaux nommés, fonctionnent sur un flux continu d'octets entre le client et le serveur. Ce flux est réalisé par un objet <xref:System.IO.Stream>. Dans une mise à niveau de flux, le client souhaite ajouter une couche de protocole facultative à la pile de canaux et demande à l'autre extrémité du canal de communication de le faire. La mise à niveau de flux consiste à remplacer l'objet <xref:System.IO.Stream> d'origine par une version mise à niveau.  
  
 Par exemple, vous pouvez générer un flux de compression directement sur le flux de transport. Dans ce cas, le <xref:System.IO.Stream> de transport d'origine est remplacé par un flux qui encapsule le <xref:System.IO.Stream> de compression autour du flux d'origine.  
  
 Vous pouvez appliquer plusieurs mises à niveau de flux, chacune encapsulant la précédente.  
  
## <a name="how-stream-upgrades-work"></a>Fonctionnement des mises à niveau de flux  

 Le processus de mise à niveau de flux comporte quatre composants.  
  
1. Un *initiateur* de flux de mise à niveau commence le processus : au moment de l’exécution, il peut lancer une requête à l’autre extrémité de sa connexion pour mettre à niveau la couche de transport de canal.  
  
2. Une mise à niveau de l' *accepteur* de flux effectue la mise à niveau : au moment de l’exécution, elle reçoit la demande de mise à niveau de l’autre ordinateur et, si possible, accepte la mise à niveau.  
  
3. Un *fournisseur* de mise à niveau crée l' *initiateur* sur le client et l' *accepteur* sur le serveur.  
  
4. Un élément de *liaison* de mise à niveau de flux est ajouté aux liaisons sur le service et le client, et crée le fournisseur au moment de l’exécution.  
  
 Notez que dans le cas de plusieurs mises à niveau, l'initiateur et l'accepteur encapsulent des ordinateurs d'état pour appliquer les transitions de mise à niveau valides pour chaque initiation.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Comment implémenter une mise à niveau de flux  

 Windows Communication Foundation (WCF) fournit quatre `abstract` classes que vous pouvez implémenter :  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Pour implémenter une mise à niveau de flux personnalisée, procédez comme suit. Cette procédure implémente un processus de mise à niveau de flux minimal sur les ordinateurs client et serveur.  
  
1. Créez une classe qui implémente <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1. Substituez la méthode <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> à appliquer au flux à mettre à niveau et retournez le flux mis à niveau. Cette méthode fonctionne de façon synchrone ; il existe des méthodes analogues pour initier la mise à niveau de façon asynchrone.  
  
    2. Substituez la méthode <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> pour rechercher des mises à niveau supplémentaires.  
  
2. Créez une classe qui implémente <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1. Substituez la méthode <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> à appliquer au flux à mettre à niveau et retournez le flux mis à niveau. Cette méthode fonctionne de façon synchrone ; il existe des méthodes analogues pour accepter la mise à niveau de façon asynchrone.  
  
    2. Substituez la méthode <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> pour déterminer si la mise à niveau demandée est prise en charge, à ce stade, par cet accepteur de mise à niveau, lors du processus de mise à niveau.  
  
3. Créez une classe qui implémente <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Substituez les méthodes <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> et <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> pour retourner des instances de l'accepteur et de l'initiateur définies aux étapes 2 et 1.  
  
4. Créez une classe qui implémente <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1. Substituez la méthode <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> sur le client et la méthode <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> sur le service.  
  
    2. Substituez la méthode <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> sur le client et la méthode <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> sur le service pour ajouter l'élément de liaison de mise à niveau à <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5. Ajoutez le nouvel élément de liaison de mise à niveau de flux aux liaisons sur les ordinateurs serveur et client.  
  
## <a name="security-upgrades"></a>Mises à niveau de sécurité  

 L'ajout d'une mise à niveau de sécurité est une version spécialisée du processus de mise à niveau de flux général.  
  
 WCF fournit déjà deux éléments de liaison pour la mise à niveau de la sécurité de flux. La configuration de sécurité au niveau du transport est encapsulée par <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> et <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> qui peuvent être configurés et ajoutés à une liaison personnalisée. Ces éléments de liaison étendent la classe <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> qui génère les fournisseurs de mise à niveau de flux client et serveur. Ces éléments de liaison ont des méthodes qui créent les classes de fournisseur de mise à niveau de flux de sécurité spécialisées, qui ne sont pas `public` ; par conséquent, dans ces deux cas, il vous suffit d’ajouter l’élément de liaison à la liaison.  
  
 Pour les scénarios de sécurité incompatibles avec les deux éléments de liaison précités, trois classes `abstract` relatives à la sécurité sont dérivées des classes de base d’initiateur, d’accepteur et de fournisseur précitées :  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Le processus d'implémentation d'une mise à niveau de flux de sécurité est le même que précédemment, à ceci près que vous dérivez les données de ces trois classes. Substituez les propriétés supplémentaires dans ces classes pour fournir des informations de sécurité au runtime.  
  
## <a name="multiple-upgrades"></a>Mises à niveau multiples  

 Pour créer des demandes de mise à niveau supplémentaires répétez le processus précité : créez des extensions supplémentaires du <xref:System.ServiceModel.Channels.StreamUpgradeProvider> et des éléments de liaison. Ajoutez les éléments de liaison à la liaison. Les éléments de liaison supplémentaires sont traités de manière séquentielle, en commençant par le premier élément de liaison ajouté à la liaison. Dans <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> et <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> chaque fournisseur de mise à niveau peut déterminer comment venir s'ajouter à tout paramètre de liaison de mise à niveau préexistant. Il doit ensuite remplacer le paramètre de liaison de mise à niveau existant par un nouveau paramètre de liaison de mise à niveau composite.  
  
 Un fournisseur de mise à niveau peut également prendre en charge plusieurs mises à niveau. Par exemple, vous pouvez souhaiter implémenter un fournisseur de mise à niveau de flux personnalisé qui prend en charge à la fois la sécurité et la compression. Procédez comme suit :  
  
1. Sous-classez <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> pour écrire la classe de fournisseur qui crée l'initiateur et l'accepteur.  
  
2. Sous-classez <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> en veillant à substituer la méthode <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> pour retourner les types de contenu pour le flux de compression et le flux sécurisé dans l'ordre.  
  
3. Sous-classez <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> qui reconnaît les types de contenu personnalisés dans sa méthode <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
4. Le flux sera mis à niveau après chaque appel à <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> et <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
