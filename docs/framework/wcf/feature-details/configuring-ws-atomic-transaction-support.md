---
title: Configuration de la prise en charge WS-Atomic Transaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 9c0e75d58fbcf61137ceae3fba9d8acfe3902171
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556588"
---
# <a name="configure-ws-atomic-transaction-support"></a>Configurer la prise en charge des transactions WS-Atomic

Cette rubrique décrit comment configurer la prise en charge WS-AtomicTransaction (WS-AT) à l'aide de l'utilitaire de configuration WS-AT.

## <a name="use-the-ws-at-configuration-utility"></a>Utiliser l’utilitaire de configuration WS-AT

L'utilitaire de configuration WS-AT (wsatConfig.exe) permet de configurer les paramètres WS-AT. Pour activer le service de protocole WS-AT, vous devez utiliser l'utilitaire de configuration pour configurer le port HTTPS pour WS-AT, lier un certificat X.509 au port HTTPS et configurer des certificats de partenaire autorisés en spécifiant des noms de sujet de certificat ou des empreintes numériques. L’utilitaire de configuration vous permet également de sélectionner le mode de suivi et de définir les délais d’attente de transaction sortants et entrants maximaux par défaut.

Vous pouvez accéder aux fonctionnalités de cet outil à l'aide d'un composant logiciel enfichable de page de propriétés MMC (Microsoft Management Console) dans la console de gestion Services de composants, ou à partir d'une fenêtre de ligne de commande. Configurez la prise en charge WS-AT sur l'ordinateur local par le biais de la fenêtre de ligne de commande ; configurez les paramètres sur les ordinateurs locaux et distants à l'aide du composant logiciel enfichable MMC.

La fenêtre de ligne de commande est accessible à l'emplacement d'installation du Kit de développement logiciel (SDK) Windows « %WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation ».

Pour plus d’informations sur l’outil en ligne de commande, consultez l' [utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md).

Si vous exécutez Windows XP ou Windows Server 2003, vous pouvez accéder au composant logiciel enfichable MMC en accédant à **panneau de configuration/outils d’administration/Services de composants**, en cliquant avec le bouton droit sur **poste de travail**, puis en sélectionnant **Propriétés**. Il s'agit du même emplacement que celui où vous pouvez configurer Microsoft Distributed Transaction Coordinator (MSDTC). Les options disponibles pour la configuration sont regroupées sous l’onglet **WS-AT** . Si vous exécutez Windows Vista ou Windows Server 2008, le composant logiciel enfichable MMC est accessible en cliquant sur le bouton **Démarrer** et en entrant `dcomcnfg.exe` dans la zone de **recherche** . À l’ouverture de la console MMC, accédez au nœud **My Travail\distributed transaction COORDINATOR\LOCAL DTC** , cliquez avec le bouton droit et sélectionnez **Propriétés**. Les options disponibles pour la configuration sont regroupées sous l’onglet **WS-AT** .

Pour plus d’informations sur le composant logiciel enfichable, consultez le [composant logiciel enfichable MMC configuration de WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md).

Pour activer l’interface utilisateur de l’outil, vous devez tout d’abord inscrire le fichier WsatUI.dll, qui se trouve à l’emplacement suivant

%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin

Pour inscrire le produit, exécutez la commande suivante depuis une fenêtre d'invite de commandes :

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a>Activer WS-AT

Pour activer le service de protocole WS-AT à l'intérieur de MSDTC à l'aide du port 443 et d'un certificat X.509 avec une clé privée installée dans le magasin de l'ordinateur local, utilisez l'outil wsatConfig.exe avec la commande suivante.

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

Remplacez les paramètres respectifs par des valeurs adaptées à votre environnement.

Pour désactiver le service de protocole WS-AT à l'intérieur de MSDTC, utilisez l'outil wsatConfig.exe avec la commande suivante.

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a>Configurer l’approbation entre deux ordinateurs

Le service de protocole WS-AT requiert que l’administrateur autorise explicitement les différents comptes à participer aux transactions distribuées. Si vous êtes administrateur de deux ordinateurs, vous pouvez configurer les deux ordinateurs de façon à établir une relation de confiance mutuelle en échangeant l'ensemble correct de certificats entre les ordinateurs, en les installant dans les magasins de certificats appropriés et en utilisant l'outil wsatConfig.exe pour ajouter le certificat de chaque ordinateur à la liste de certificats de participants autorisés de l'autre ordinateur. Cette étape est nécessaire pour exécuter des transactions distribuées entre deux ordinateurs à l'aide de WS-AT.

L'exemple suivant illustre les étapes requises pour établir la confiance entre deux ordinateurs, A et B.

### <a name="create-and-export-certificates"></a>Créer et exporter des certificats

Cette procédure requiert le composant logiciel enfichable MMC Certificats. Ce composant logiciel enfichable est accessible en ouvrant le menu Démarrer/Exécuter, en tapant « mmc » dans la zone d'entrée et en appuyant sur OK. Ensuite, dans la fenêtre **Console1** , accédez au composant logiciel enfichable **fichier/ajouter-supprimer** , cliquez sur Ajouter, puis choisissez **certificats** dans la liste **composants logiciels enfichables autonome disponible** . Enfin, sélectionnez le **compte d’ordinateur** à gérer, puis cliquez sur **OK**. Le nœud **certificats** apparaît dans la console du composant logiciel enfichable.

Vous devez déjà posséder les certificats requis pour établir la confiance. Pour savoir comment créer et installer de nouveaux certificats avant les étapes suivantes, consultez [procédure : créer et installer des certificats clients temporaires dans WCF pendant le développement](/previous-versions/msp-n-p/ff650751(v=pandp.10)).

1. Sur l'ordinateur A, à l'aide du composant logiciel enfichable MMC Certificats, importez le certificat existant (certA) dans les magasins LocalMachine\MY (Nœud personnel) et LocalMachine\ROOT (nœud de l'Autorité de certification racine de confiance). Pour importer un certificat vers un nœud spécifique, cliquez avec le bouton droit sur le nœud et choisissez **toutes les tâches/importer**.

2. Sur l'ordinateur B, à l'aide du composant logiciel enfichable MMC Certificats, créez ou obtenez un certificat certB avec une clé privée et importez-le dans les magasins LocalMachine\MY (Nœud personnel) et LocalMachine\ROOT (nœud de l'Autorité de certification racine de confiance).

3. Exportez la clé publique de certA dans un fichier si cela n'a pas déjà été fait.

4. Exportez la clé publique de certB dans un fichier si cela n'a pas déjà été fait.

### <a name="establish-mutual-trust-between-machines"></a>Établir une approbation mutuelle entre les machines

1. Sur l'ordinateur A, importez la représentation de fichier de certB dans les magasins LocalMachine\MY et LocalMachine\ROOT. Cela déclare que l'ordinateur A approuve certB pour toute communication.

2. Sur l'ordinateur B, importez le fichier certA dans les magasins LocalMachine\MY et LocalMachine\ROOT. Cela implique que l'ordinateur B approuve certA pour toute communication.

Après avoir effectué ces étapes, la confiance est établie entre les deux ordinateurs et ils peuvent être configurés pour communiquer l'un avec l'autre à l'aide de WS-AT.

### <a name="configure-msdtc-to-use-certificates"></a>Configurer MSDTC pour utiliser des certificats

Le service de protocole WS-AT agissant à la fois comme client et comme serveur, il doit à la fois écouter les connexions entrantes et initier les connexions sortantes. Par conséquent, vous devez configurer MSDTC de sorte qu'il sache quel certificat utiliser lors des communications avec les correspondants externes, et quels certificats autoriser lors de l'acceptation des communications entrantes.

Vous pouvez configurer cela à l'aide du composant logiciel enfichable MMC WS-AT. Pour plus d’informations sur cet outil, consultez la rubrique [composant logiciel enfichable MMC configuration de WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md) . Les étapes suivantes décrivent comment établir la confiance entre deux ordinateurs qui exécutent MSDTC.

1. Configurez les paramètres de l'ordinateur A. Pour « certificat de point de terminaison », sélectionnez certa. Pour « certificats autorisés », sélectionnez certB.

2. Configurez les paramètres de l'ordinateur B. Pour « certificat de point de terminaison », sélectionnez certB. Pour « certificats autorisés », sélectionnez le certificat certa.

> [!NOTE]
> Lorsqu'un ordinateur envoie un message à l'autre ordinateur, l'expéditeur essaie de vérifier que le nom du sujet du certificat du destinataire et le nom d'ordinateur du destinataire correspondent. S'ils ne correspondent pas, la vérification de certificat échoue et les deux ordinateurs ne peuvent pas communiquer.
>
> Pour un ordinateur joint à un domaine, le nom est le nom de domaine complet. Par défaut, le nom d'un ordinateur sur un groupe de travail est le nom NetBIOS de l'ordinateur. Toutefois, le nom peut également inclure un suffixe DNS (Domain Name System) s'il y en a un présent pour la connexion utilisée entre les deux ordinateurs.
>
> Si le nom de l'ordinateur change, par exemple lorsqu'un ordinateur de groupe de travail rejoint un domaine, vous devez rééditer les certificats ou configurer manuellement les suffixes DNS.

## <a name="security"></a>Sécurité

Étant donné que certains des paramètres liés à MSDTC et WS-AT sont stockés dans le Registre, respectivement aux emplacements HKLM\Software\Microsoft\MSDTC et HKLM\Software\Microsoft\WSAT, assurez-vous que ces clés de Registre sont sécurisées afin que seuls les administrateurs puissent y écrire. Dans l’outil Éditeur du Registre, cliquez avec le bouton droit sur la clé que vous souhaitez sécuriser, puis sélectionnez **autorisation** pour définir le contrôle d’accès approprié. Il est essentiel pour la sécurité et l'intégrité du système que les clés importantes soient en lecture seule pour les utilisateurs à faible privilège.

Lors du déploiement de MSDTC, l'administrateur doit s'assurer que tout échange de données MSDTC est sécurisé. Dans un déploiement de groupe de travail, isolez l'infrastructure transactionnelle des utilisateurs malveillants ; dans un déploiement de cluster, sécurisez le Registre de cluster.

## <a name="tracing"></a>Traçage

Le service de protocole WS-AT prend en charge le suivi intégré, spécifique aux transactions, qui peut être activé et géré par le biais de l’outil de [composant logiciel enfichable MMC configuration de WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md) . Les suivis peuvent inclure des données qui indiquent l'heure d'une inscription pour une transaction spécifique, l'heure à laquelle une transaction atteint son état terminal, le résultat que chaque inscription de transaction a reçu. Toutes les traces peuvent être affichées à l’aide de l’outil [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .

Le service de protocole WS-AT prend en charge également le suivi ServiceModel intégré sur l'ensemble de la session de suivi ETW. Cela procure des suivis plus détaillés et spécifiques à la communication, en plus des suivis de transaction existants.  Pour activer ces suivis supplémentaires, procédez comme suit

1. Ouvrez le menu **Démarrer/Exécuter** , tapez « regedit » dans la zone d’entrée, puis sélectionnez **OK**.

2. Dans l' **éditeur du Registre**, accédez au dossier suivant dans le volet gauche, HKEY_LOCAL_MACHINE \software\microsoft\wsat\3.0\

3. Cliquez avec le bouton droit sur la `ServiceModelDiagnosticTracing` valeur dans le volet droit, puis sélectionnez **modifier**.

4. Dans la zone entrée de données de la **valeur** , entrez l’une des valeurs valides suivantes pour spécifier le niveau de suivi que vous souhaitez activer.

- 0 : désactivé

- 1 : critique

- 3 : erreur. Il s'agit de la valeur par défaut

- 7 : avertissement

- 15 : informations

- 31 : en clair

## <a name="see-also"></a>Voir aussi

- [Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Composant logiciel enfichable MMC Configuration WS-AtomicTransaction](../ws-atomictransaction-configuration-mmc-snap-in.md)
