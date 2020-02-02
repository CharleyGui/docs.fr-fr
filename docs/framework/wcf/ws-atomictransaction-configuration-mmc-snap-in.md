---
title: Composant logiciel enfichable MMC Configuration WS-AtomicTransaction
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 0bcd08f9a3450c850ead941df6313526d076df2d
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921347"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Composant logiciel enfichable MMC configuration WS-AtomicTransaction

Le composant logiciel enfichable MMC configuration de WS-AtomicTransaction est utilisé pour configurer une partie des paramètres WS-AtomicTransaction sur les ordinateurs locaux et distants.

## <a name="remarks"></a>Notes

Si vous exécutez Windows XP ou Windows Server 2003, vous pouvez trouver le composant logiciel enfichable MMC en accédant à **panneau de configuration/outils d’administration/Services de composants/** , en cliquant avec le bouton droit sur **poste de travail**, puis en sélectionnant **Propriétés**. C'est le même emplacement que celui dans lequel vous pouvez configurer le MSDTC. Les options disponibles pour la configuration sont regroupées sous l’onglet **WS-AT** .

 Si vous exécutez Windows Vista ou Windows Server 2008, vous pouvez trouver le composant logiciel enfichable MMC en cliquant sur le bouton **Démarrer** et en tapant `dcomcnfg.exe` dans la zone de **recherche** . À l’ouverture de la console MMC, accédez au nœud **My Travail\distributed transaction COORDINATOR\LOCAL DTC** , cliquez avec le bouton droit et sélectionnez **Propriétés**. Les options disponibles pour la configuration sont regroupées sous l’onglet **WS-AT** .

 Les étapes précédentes sont utilisées pour lancer le composant logiciel enfichable afin de configurer un ordinateur local. Si vous souhaitez configurer un ordinateur distant, vous devez rechercher le nom de l’ordinateur distant dans **panneau de configuration/outils d’administration/Services de composants/** , et effectuer les mêmes étapes si vous exécutez Windows XP ou windows Server 2003. Si vous exécutez Windows Vista ou Windows Server 2008, suivez les étapes précédentes pour Vista et Windows Server 2008, mais utilisez le nœud **DTC Coordinator\Local Distributed Transaction** sous le nœud de l’ordinateur distant.

 Pour utiliser l'interface utilisateur fournie par l'outil, vous devez enregistrer le fichier WsatUI.dll, situé à l'emplacement suivant :

 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**

 L'inscription peut être faite par la commande suivante.

```console
regasm.exe /codebase WsatUI.dll
```

 Vous pouvez utiliser cet outil pour modifier les paramètres de base WS-AtomicTransaction. Par exemple, vous pouvez activer et désactiver le support de protocole de WS-AtomicTransaction, configurer les ports HTTP pour WS-AT, lier un certificat SSL au port HTTP, configurer des certificats en spécifiant les noms de sujet correspondants, sélectionner le mode de suivi et définir la valeur par défaut et les délais d'attente maximum.

 Si vous devez configurer la prise en charge de WS-AtomicTransaction sur l’ordinateur local uniquement, vous pouvez utiliser la version de ligne de commande de cet outil. Pour plus d’informations sur l’outil en ligne de commande, consultez la rubrique [utilitaire de configuration WS-AtomicTransaction (WsatConfig. exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) .

 Sachez que le composant logiciel enfichable MMC et l'outil de ligne de commande ne prennent pas en charge la configuration de tous les paramètres WS-AT. Ces paramètres ne peuvent être modifiés qu'en modifiant directement le registre. Pour plus d’informations sur ces paramètres de Registre, consultez Configuration de la [prise en charge des transactions WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md).

### <a name="user-interface-description"></a>Description de l'interface utilisateur

**Activer la prise en charge du réseau WS-Atomic Transaction**:

 Lorsque vous sélectionnez ou désélectionnez cette case à cocher, cela active ou désactive tous les composants d'interface utilisateur de ce composant logiciel enfichable.

 Avant d'activer cette case à cocher, vous devez vous assurer que l'accès au réseau DTC est activé (communications entrantes ou sortantes, ou encore les deux). Cette valeur peut être vérifiée sous l’onglet **sécurité** du composant logiciel enfichable MSDTC.

#### <a name="network-group-box"></a>Zone de groupe Réseau

Vous pouvez spécifier le port HTTPS et des paramètres de sécurité supplémentaires, tels que le chiffrement SSL dans le groupe Réseau. Ce groupe est désactivé (grisé) si les transactions réseau DTC ne sont pas activées.

 **Port HTTPs**

 C'est la valeur du port HTTPS utilisée pour WS-AT. Cette valeur doit être un nombre compris dans la plage 1-65535 (pour représenter un port valide). La modification du port HTTP modifie la configuration du service HTTP, ce qui signifie que l’adresse de service WS-AT utilisée précédemment est libérée et qu’une nouvelle adresse de service WS-AT est enregistrée sur la base du nouveau port. De plus, le port que vous venez de sélectionner est chiffré avec le certificat sélectionné pour le chiffrement SSL.

> [!NOTE]
> Si vous avez déjà activé le pare-feu avant d'exécuter cet outil, le port est enregistré automatiquement dans la liste d'exceptions. Si le pare-feu est désactivé avant l'exécution de cet outil, aucun élément supplémentaire n'est configuré concernant le pare-feu.

 Si vous activez le pare-feu après avoir configuré WS-AT, vous devez réexécuter cet outil et fournir le numéro de port à l'aide de ce paramètre. Si vous désactivez le pare-feu après la configuration, WS-AT continue à fonctionner sans entrée supplémentaire.

 **Certificat de point de terminaison**

 Le fait de cliquer sur le bouton **Sélectionner** affiche une liste des certificats actuellement disponibles sur l’ordinateur local, ce qui permet à l’utilisateur de sélectionner le certificat qui peut être utilisé pour le chiffrement SSL. Les certificats doivent posséder une clé privée. Si ce n'est pas le cas, un message d'erreur s'affiche.

> [!NOTE]
> Lorsque vous définissez un certificat SSL pour un port sélectionné, vous remplacez le certificat SSL d’origine associé à ce port, le cas échéant.

 **Comptes autorisés**

 Le fait de cliquer sur le bouton **Sélectionner** appelle l’éditeur de liste de Access Control Windows, où vous pouvez spécifier l’utilisateur ou le groupe qui peut participer à des transactions WS-Atomic en activant la case à cocher **autoriser** ou **refuser** dans le groupe d’autorisations **participer** .

 **Certificats autorisés**

 Cliquez sur le bouton **Sélectionner** pour afficher la liste des certificats actuellement disponibles sur l’ordinateur LocalMachine. Vous pouvez sélectionner ensuite les identités de certificat autorisées à participer à WS-AtomicTransaction.

#### <a name="timeout-group-box"></a>Zone de groupe Délai d'attente

La zone de groupe **délai d’attente** vous permet de spécifier le délai d’expiration par défaut et maximal pour une transaction WS-Atomic. Les valeurs valides de délai d'attente sortant sont comprises entre 1 et 3 600. Les valeurs valides de délai d'attente entrant sont comprises entre 0 et 3 600.

#### <a name="tracing-and-logging-group-box"></a>Zone de groupe Suivi et journalisation

La zone de groupe **suivi et journalisation** vous permet de configurer le niveau de suivi et de journalisation souhaité.

 Cliquez sur le bouton **options** pour appeler une page dans laquelle vous pouvez spécifier des paramètres supplémentaires.

 La zone de combinaison **niveau de suivi** vous permet de choisir parmi toute valeur valide de l’énumération <xref:System.Diagnostics.TraceLevel>. Vous pouvez également utiliser les cases à cocher pour spécifier si vous souhaitez exécuter le suivi des activités, la propagation d'activité ou le rassemblement d'informations d'identification personnelles (PII).

 Vous pouvez également spécifier des sessions de journalisation dans la zone de groupe **session de journalisation** .

> [!NOTE]
> Lorsqu'un autre consommateur de suivi utilise le fournisseur de suivi WS-AT, vous ne pouvez pas créer de nouvelle session de journalisation pour les événements de suivi. Toute tentative de configuration de la journalisation pendant cette période aboutit à l'affichage du message d'erreur suivant : Impossible d'activer le fournisseur. Code d'erreur :1

 Pour plus d’informations sur le suivi et la journalisation, consultez [administration et diagnostics](./diagnostics/index.md).

## <a name="see-also"></a>Voir aussi

- [Configuration de la prise en charge WS-Atomic Transaction](./feature-details/configuring-ws-atomic-transaction-support.md)
- [Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Administration et diagnostics](./diagnostics/index.md)
