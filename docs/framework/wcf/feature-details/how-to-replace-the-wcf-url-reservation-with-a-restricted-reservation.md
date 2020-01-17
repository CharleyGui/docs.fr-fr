---
title: "Procédure : remplacer la réservation d'URL WCF par une réservation restreinte"
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: fc50a0e31a0c323b695ada6565743fa19c1d4c2a
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212191"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Procédure : remplacer la réservation d'URL WCF par une réservation restreinte

Une réservation d'URL vous permet de limiter les personnes qui reçoivent les messages d'une URL ou d'un jeu d'URL. Une réservation se compose d'un modèle d'URL, d'une liste de contrôle d'accès (ACL) et d'un jeu d'indicateurs. Le modèle d'URL définit les URL affectées par la réservation. Pour plus d’informations sur le traitement des modèles d’URL, consultez [routage des demandes entrantes](/windows/win32/http/routing-incoming-requests). L'ACL contrôle quel utilisateur ou groupe d'utilisateurs est autorisé à recevoir des messages en provenance des URL spécifiées. Les indicateurs spécifient si la réservation consiste à donner directement à un utilisateur ou à un groupe l'autorisation d'écouter l'URL ou à déléguer l'autorisation d'écouter à d'autres processus.  
  
 Dans le cadre de la configuration du système d’exploitation par défaut, Windows Communication Foundation (WCF) crée une réservation accessible globalement pour le port 80 afin de permettre à tous les utilisateurs d’exécuter des applications qui utilisent une liaison HTTP double pour la communication duplex. Étant donné que l'ACL sur cette réservation concerne tous les utilisateurs, les administrateurs ne peuvent pas explicitement accorder ou refuser l'autorisation d'écouter une URL ou un jeu d'URL. Cette rubrique explique comment supprimer cette réservation et comment la recréer avec une ACL restreinte.  
  
Sur Windows Vista ou Windows Server 2008, vous pouvez afficher toutes les réservations d’URL HTTP à partir d’une invite de commandes avec élévation de privilèges en entrant `netsh http show urlacl`. L’exemple suivant montre à quoi doit ressembler une réservation d’URL WCF :

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 La réservation se compose d’un modèle d’URL utilisé lorsqu’une application WCF utilise une liaison HTTP double pour la communication duplex. Les URL de ce formulaire sont utilisées pour qu’un service WCF renvoie des messages au client WCF lors de la communication sur une liaison double HTTP. Tous les utilisateurs sont autorisés à écouter l'URL, mais pas à déléguer l'écoute à un autre processus. Enfin, l'ACL est décrite en langage SDDL (Security Descriptor Definition Language). Pour plus d’informations sur SSDL, consultez [SSDL](/windows/win32/secauthz/security-descriptor-definition-language) .  
  
## <a name="to-delete-the-wcf-url-reservation"></a>Pour supprimer la réservation d'URL WCF  
  
1. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **accessoires**, cliquez avec le bouton droit sur invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur** dans le menu contextuel qui s' **affiche** . Cliquez sur **Continuer** dans la fenêtre contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2. Dans la fenêtre d’invite de commandes, tapez **netsh http Delete urlacl url =http://+:80/Temporary_Listen_Addresses/** .  
  
3. Si la réservation est supprimée avec succès, le message suivant s'affiche. **La réservation d’URL a été supprimée**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Création d'un nouveau groupe de sécurité et d'une nouvelle réservation d'URL restreinte  
 Pour remplacer la réservation d’URL WCF par une réservation restreinte, vous devez d’abord créer un nouveau groupe de sécurité. Pour ce faire, deux méthodes s'offrent à vous : à partir d'une invite de commandes ou de la console de gestion de l'ordinateur. L'utilisation d'une seule de ces méthodes suffit.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Pour créer un groupe de sécurité à partir d'une invite de commandes  
  
1. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **accessoires**, cliquez avec le bouton droit sur invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur** dans le menu contextuel qui s' **affiche** . Cliquez sur **Continuer** dans la fenêtre contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2. Tapez **net localgroup "\<nom du groupe de sécurité >"/Comment : "\<Description du groupe de sécurité >"/Add** à l’invite de commandes. Remplacez **\<nom du groupe de sécurité >** par le nom du groupe de sécurité que vous souhaitez créer et **\<Description du groupe de sécurité >** par une description appropriée du groupe de sécurité.  
  
3. Si le groupe de sécurité est créé avec succès, le message suivant s'affiche. **La commande s’est terminée avec succès.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Pour créer un groupe de sécurité à partir de la console de gestion de l'ordinateur  
  
1. Cliquez sur **Démarrer**, sur **panneau de configuration**, sur **Outils d’administration**, puis sur gestion de l' **ordinateur** pour ouvrir la console de gestion de l’ordinateur. Cliquez sur **Continuer** dans la fenêtre contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2. Cliquez sur **Outils système**, sur **utilisateurs et groupes locaux**, cliquez avec le bouton droit sur le dossier **groupes** , puis cliquez sur **nouveau groupe** dans le menu contextuel qui s’affiche. Tapez le nom de **groupe**, la **Description** et d’autres détails souhaités pour ce nouveau groupe de sécurité, puis cliquez sur le bouton **créer** pour créer le groupe de sécurité.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Pour créer la réservation d'URL restreinte  
  
1. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **accessoires**, cliquez avec le bouton droit sur invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur** dans le menu contextuel qui s' **affiche** . Cliquez sur **Continuer** dans la fenêtre contrôle de compte d’utilisateur (UAC) qui peut demander des autorisations pour continuer.  
  
2. Dans l’invite de commandes, tapez **netsh http add urlacl url =http://+:80/Temporary_Listen_Addresses/ user = "\< nom de l’ordinateur >\\ < nom du groupe de sécurité\>** . En remplaçant **\<nom** de l’ordinateur > par le nom de l’ordinateur sur lequel le groupe doit être créé et **\<nom du groupe de sécurité >** par le nom du groupe de sécurité que vous avez créé précédemment.  
  
3. Si la réservation est créée avec succès, le message suivant s'affiche. La **réservation d’URL a été ajoutée**.
