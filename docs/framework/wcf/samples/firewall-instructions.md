---
title: Instructions sur les pare-feu
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 06e5ba64ab0ec3558e4c773c9cb21f961384e0c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650042"
---
# <a name="firewall-instructions"></a>Instructions sur les pare-feu
Vous devez activer plusieurs ports ou programmes dans le pare-feu pour que les exemples Windows Communication Foundation (WCF) peuvent fonctionner. Un grand nombre d'exemples communique en utilisant des ports contenus dans la plage 8000-8003, ainsi que le port 9000. Le pare-feu est activé par défaut et empêche l'accès à ces ports. Pour activer le pare-feu pour les exemples, exécutez l’une des procédures suivantes, selon vos besoins et votre environnement de sécurité :  
  
- Option 1 : Activation interactive des exemples en cours d’exécution. N'apportez aucune modification à l'avance à votre configuration de pare-feu et lancez la création et l'exécution des exemples. Lorsqu’un exemple est exécuté, un **alerte de sécurité Windows** boîte de dialogue s’affiche. L'exemple de programme en question peut ensuite être ajouté interactivement à une liste non bloquée. Dans le cadre de cette procédure, vous devrez peut-être redémarrer l'exemple.  
  
- Option 2 : Activer les exemples de programmes à l’avance. Démarrer le **le panneau de configuration pare-feu Windows** applet et activer les exemples de programmes que vous prévoyez d’exécuter. Vous devez générer en premier les programmes afin que les fichiers exécutables existent. Vous trouverez des instructions plus détaillées dans la procédure suivante.  
  
- Option 3 : Activer une plage de ports à l’avance. Démarrer le **Windows Firewall** **le panneau de configuration** applet et activer les ports 80, 443, 8000-8003 et 9000, qui sont utilisés par les exemples. Vous trouverez des instructions plus détaillées dans la procédure suivante. Cette option est moins sécurisée que les autres, car elle permet à tout programme d'utiliser ces ports, et non aux exemples uniquement.  
  
 Si vous ne savez pas quelle procédure utiliser, choisissez la première option. Si vous utilisez le pare-feu d'un autre fournisseur, vous devrez peut-être apporter des modifications semblables.  
  
> [!IMPORTANT]
>  La modification de votre configuration de pare-feu affecte votre sécurité. Il est recommandé d'enregistrer les modifications apportées et de les supprimer lorsque vous n'utilisez plus les exemples.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Pour activer à l'avance les programmes d'exemples  
  
1. Créez un exemple.  
  
2. Cliquez sur **Démarrer**, cliquez sur **exécuter**et le type `firewall.cpl`. Cette opération ouvre le **le panneau de configuration pare-feu Windows** applet.  
  
    > [!NOTE]
    >  Pour exécuter des exemples qui requièrent la capacité de communiquer via le Pare-feu Windows, vous devez disposer des autorisations nécessaires pour modifier les paramètres du Pare-feu Windows. Si certains paramètres du pare-feu ne sont pas disponibles et que votre ordinateur est connecté à un domaine, il est possible que votre administrateur système contrôle ces paramètres au moyen d'une stratégie de groupe.  
  
3. Effectuez l'une des étapes suivantes, selon votre système d'exploitation, pour autoriser un programme via le Pare-feu Windows :  
  
    - Dans Windows 7 ou Windows Server 2008 r2, cliquez sur **permettent à un programme ou une fonctionnalité via le pare-feu de Windows**. Cliquez sur **modifier les paramètres**, autoriser **un autre programme...** .  
  
    - Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], cliquez sur **autoriser un programme via le pare-feu de Windows**.  
  
4. Sur le **Exceptions** , cliquez sur **ajouter un programme**.  
  
5. Cliquez sur le **Parcourir** bouton et sélectionnez le fichier exécutable de l’exemple que vous projetez d’exécuter.  
  
6. Répétez les étapes 4 et 5 jusqu'à ce que vous avez ajouté les fichiers exécutables de tous les échantillons que vous projetez d’exécuter.  
  
7. Cliquez sur **OK** pour fermer l’applet de pare-feu.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Pour activer une plage de ports à l'avance  
  
1. Cliquez sur **Démarrer**, cliquez sur **exécuter**et le type `firewall.cpl`. Cette opération ouvre le **le panneau de configuration pare-feu Windows** applet.  
  
2. Sur Windows 7 ou Windows Server 2008 R2, procédez comme suit.  
  
    1. Cliquez sur **paramètres avancés** dans la colonne de gauche de la fenêtre de pare-feu de Windows.  
  
    2. Cliquez sur **règles de trafic entrant** dans la colonne de gauche.  
  
    3. Cliquez sur **nouvelles règles** dans la colonne de droite.  
  
    4. Sélectionnez **Port** et cliquez sur **suivant**.  
  
    5. Sélectionnez **TCP** et entrez `8000, 8001, 8002, 8003, 9000, 80, 443` dans le **ports locaux spécifiques** champ.  
  
    6. Cliquez sur **Suivant**.  
  
    7. Sélectionnez **autoriser la connexion**, puis cliquez sur **suivant** .  
  
    8. Sélectionnez **domaine** et **privé**, puis cliquez sur **suivant**.  
  
    9. Nommez cette règle `WCF-WF 4.0 Samples`, puis cliquez sur **Terminer**.  
  
    10. Cliquez sur **règles de trafic sortant** et répétez les étapes c à h.  
  
3. Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], procédez comme suit.  
  
    1. Cliquez sur **autoriser un programme via le pare-feu de Windows**.  
  
    2. Sur le **Exceptions** , cliquez sur **ajouter un Port**.  
  
    3. Entrez un nom, entrez le numéro de port 8000 et sélectionnez le **TCP** option.  
  
    4. Cliquez sur le **modifier l’étendue** bouton, sélectionnez le **mon réseau** seule option disponible (sous-réseau), puis cliquez sur **OK**.  
  
    5. Répétez les étapes b à d pour les ports 8001, 8002, 8003, 9000, 80 et 443.  
  
4. Cliquez sur **OK** pour fermer l’applet de pare-feu.  
  
> [!NOTE]
>  Supprimez toutes les exceptions de pare-feu une fois que vous n'utilisez plus les exemples. Pour ce faire, ouvrez le **le panneau de configuration pare-feu Windows** applet et supprimez tous les programmes ou entrées qui ont été ajoutées par les procédures précédentes de port.
