---
title: Instructions sur les pare-feu
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 2c07d17ebb6bbefa78d12bb128e354112311891a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044949"
---
# <a name="firewall-instructions"></a>Instructions sur les pare-feu
Vous devez activer plusieurs ports ou programmes dans le pare-feu pour que les exemples Windows Communication Foundation (WCF) puissent fonctionner. Un grand nombre d'exemples communique en utilisant des ports contenus dans la plage 8000-8003, ainsi que le port 9000. Le pare-feu est activé par défaut et empêche l'accès à ces ports. Pour activer le pare-feu pour les exemples, exécutez l’une des procédures suivantes, selon vos besoins et votre environnement de sécurité :  
  
- Option 1 : Active les exemples en cours d’exécution. N'apportez aucune modification à l'avance à votre configuration de pare-feu et lancez la création et l'exécution des exemples. Quand un exemple est exécuté, une boîte de dialogue **alerte de sécurité Windows** s’affiche. L'exemple de programme en question peut ensuite être ajouté interactivement à une liste non bloquée. Dans le cadre de cette procédure, vous devrez peut-être redémarrer l'exemple.  
  
- Option 2 : Activez les exemples de programmes à l’avance. Démarrez l’applet du **panneau de configuration du pare-feu Windows** et activez les exemples de programmes que vous prévoyez d’exécuter. Vous devez générer en premier les programmes afin que les fichiers exécutables existent. Vous trouverez des instructions plus détaillées dans la procédure suivante.  
  
- Option 3 : Activez une plage de ports à l’avance. Démarrez l’applet du **panneau de configuration** du **pare-feu Windows** et activez les ports 80, 443, 8000-8003 et 9000, qui sont utilisés par les exemples. Vous trouverez des instructions plus détaillées dans la procédure suivante. Cette option est moins sécurisée que les autres, car elle permet à tout programme d'utiliser ces ports, et non aux exemples uniquement.  
  
 Si vous ne savez pas quelle procédure utiliser, choisissez la première option. Si vous utilisez le pare-feu d'un autre fournisseur, vous devrez peut-être apporter des modifications semblables.  
  
> [!IMPORTANT]
> La modification de votre configuration de pare-feu affecte votre sécurité. Il est recommandé d'enregistrer les modifications apportées et de les supprimer lorsque vous n'utilisez plus les exemples.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Pour activer à l'avance les programmes d'exemples  
  
1. Créez un exemple.  
  
2. Cliquez sur **Démarrer**, sur **exécuter**, puis `firewall.cpl`tapez. L’applet du **panneau de configuration du pare-feu Windows** s’ouvre.  
  
    > [!NOTE]
    > Pour exécuter des exemples qui requièrent la capacité de communiquer via le Pare-feu Windows, vous devez disposer des autorisations nécessaires pour modifier les paramètres du Pare-feu Windows. Si certains paramètres du pare-feu ne sont pas disponibles et que votre ordinateur est connecté à un domaine, il est possible que votre administrateur système contrôle ces paramètres au moyen d'une stratégie de groupe.  
  
3. Effectuez l'une des étapes suivantes, selon votre système d'exploitation, pour autoriser un programme via le Pare-feu Windows :  
  
    - Sur Windows 7 ou Windows Server 2008 R2, cliquez sur **autoriser un programme ou une fonctionnalité via le pare-feu Windows**. Cliquez sur **modifier les paramètres**, autoriser **un autre programme...** .  
  
    - Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou[!INCLUDE[lserver](../../../../includes/lserver-md.md)], cliquez sur **autoriser un programme via le pare-feu Windows**.  
  
4. Sous l’onglet **exceptions** , cliquez sur **Ajouter un programme**.  
  
5. Cliquez sur le bouton **Parcourir** et sélectionnez le fichier exécutable de l’exemple que vous prévoyez d’exécuter.  
  
6. Répétez les étapes 4 et 5 jusqu’à ce que vous ayez ajouté les fichiers exécutables de tous les exemples que vous prévoyez d’exécuter.  
  
7. Cliquez sur **OK** pour fermer l’applet de pare-feu.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Pour activer une plage de ports à l'avance  
  
1. Cliquez sur **Démarrer**, sur **exécuter**, puis `firewall.cpl`tapez. L’applet du **panneau de configuration du pare-feu Windows** s’ouvre.  
  
2. Sur Windows 7 ou Windows Server 2008 R2, procédez comme suit.  
  
    1. Cliquez sur **Paramètres avancés** dans la colonne de gauche de la fenêtre du pare-feu Windows.  
  
    2. Dans la colonne de gauche, cliquez sur **règles de trafic entrant** .  
  
    3. Cliquez sur **nouvelles règles** dans la colonne de droite.  
  
    4. Sélectionnez **port** et cliquez sur **suivant**.  
  
    5. Sélectionnez **TCP** et entrez `8000, 8001, 8002, 8003, 9000, 80, 443` dans le champ **ports locaux spécifiques** .  
  
    6. Cliquez sur **Suivant**.  
  
    7. Sélectionnez **autoriser la connexion**, puis cliquez sur **suivant** .  
  
    8. Sélectionnez **domaine** et **privé**, puis cliquez sur **suivant**.  
  
    9. Nommez cette `WCF-WF 4.0 Samples`règle, puis cliquez sur **Terminer**.  
  
    10. Cliquez sur **règles de trafic sortant** et répétez les étapes c à h.  
  
3. Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], procédez comme suit.  
  
    1. Cliquez sur **autoriser un programme via le pare-feu Windows**.  
  
    2. Sous l’onglet **exceptions** , cliquez sur **Ajouter un port**.  
  
    3. Entrez un nom, entrez 8000 comme numéro de port, puis sélectionnez l’option **TCP** .  
  
    4. Cliquez sur le bouton **modifier l’étendue** , sélectionnez l’option **mon réseau** (sous-réseau uniquement), puis cliquez sur **OK**.  
  
    5. Répétez les étapes b à d pour les ports 8001, 8002, 8003, 9000, 80 et 443.  
  
4. Cliquez sur **OK** pour fermer l’applet de pare-feu.  
  
> [!NOTE]
> Supprimez toutes les exceptions de pare-feu une fois que vous n'utilisez plus les exemples. Pour ce faire, ouvrez l’applet du **panneau de configuration du pare-feu Windows** et supprimez tous les programmes ou entrées de port ajoutés par les procédures précédentes.
