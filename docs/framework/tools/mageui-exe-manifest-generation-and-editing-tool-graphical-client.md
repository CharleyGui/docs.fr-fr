---
title: MageUI.exe (outil Manifest Generation and Editing, client graphique)
description: Explorez MageUI.exe, le Outil Manifest Generation and Editing, le client graphique. Créez, modifiez et signez les manifestes de déploiement et d’application avec cet outil GUI.
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 59f2d3dbf09beacb62042b8195bba23f345fba02
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557435"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (outil Manifest Generation and Editing, client graphique)

MageUI.exe prend en charge les mêmes fonctionnalités que l'outil de ligne de commande Mage.exe, mais avec une interface utilisateur Windows. Avec cet outil, vous pouvez créer, modifier et signer les manifestes de déploiement et d'application. Les nouveaux manifestes créés avec MageUI.exe ciblent le profil client .NET Framework 4. Les versions antérieures de MageUI.exe doivent être utilisées pour cibler des versions précédentes de .NET Framework. Lors de l’ajout ou de la suppression d’assemblys dans un manifeste, ou lors de la nouvelle signature de manifestes existants, MageUI.exe ne met pas à jour le manifeste pour cibler .NET Framework 4 Client Profile. Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](mage-exe-manifest-generation-and-editing-tool.md).

 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

 Deux versions de Mage.exe et MageUI.exe sont incluses en tant que composant d’installation de Visual Studio. Pour afficher les informations de version, exécutez MageUI.exe, sélectionnez **aide**, puis cliquez **sur à propos**de. Cette documentation décrit la version 4.0.x.x de Mage.exe et MageUI.exe.

> [!NOTE]
> MageUI.exe ne prend pas en charge l’élément [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) lors de l’enregistrement d’un manifeste d’application qui a déjà été signé avec un certificat utilisant MageUI.exe. À la place, vous devez utiliser [Mage.exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Le tableau ci-dessous répertorie les éléments de menu et de barre d'outils disponibles.  
  
|Commande|Menu|Raccourci|Description|  
|-------------|----------|--------------|-----------------|  
|**Manifeste d’application**|**Fichier, nouveau**||Crée un nouveau manifeste d'application.|  
|**Manifeste de déploiement**|**Fichier, nouveau**||Crée un nouveau manifeste de déploiement.|  
|**Ouvrir**|**File**|Ctrl+O|Ouvre un manifeste de déploiement, un manifeste d'application ou une licence de confiance existant à modifier.|  
|**Close**|**File**|Ctrl+F4|Ferme un fichier ouvert.<br /><br /> Si vous modifiez un fichier avant de le fermer, MageUI.exe vous invite à resigner le fichier avec une clé publique, une paire de clés ou un certificat stocké.|  
|**Save**|**File**|Ctrl+S|Enregistre sur le disque le document qui possède actuellement le focus d'entrée utilisateur.|  
|**Enregistrer sous**|**File**||Enregistre un fichier sur le disque, en vous permettant de fournir un nouveau nom et/ou emplacement de fichier.|  
|**Enregistrer tout**|**File**||Enregistre les modifications apportées à tous les fichiers actuellement ouverts dans MageUI.exe.|  
|**Préférences**|**File**||Ouvre la boîte de dialogue **Préférences**. Pour plus d'informations, consultez la section suivante.|  
|**Quitter**|**File**|ALT+F4|Quitte MageUI.exe.|  
|**Couper**|**Modifier**|Ctrl+X|Supprime le texte actuellement sélectionné de l'application et le déplace dans le Presse-papiers du système.|  
|**Copy**|**Modifier**|CTRL+C|Copie le texte actuellement sélectionné dans le Presse-papiers du système.|  
|**Coller**|**Modifier**|Ctrl+V|Colle le texte du Presse-papiers du système dans l'élément texte actif.|  
|**Supprimer**|**Modifier**||Supprime un élément actuellement sélectionné dans une liste, comme une licence de confiance dans l’onglet **Manifeste de déploiement**.|  
|**Fermer tout**|**Window**||Ferme tous les fichiers actuellement ouverts dans MageUI.exe. Si un ou plusieurs fichiers ont besoin de l'enregistrement, MageUI.exe vous invite à les enregistrer. MageUI.exe vous demande également de sélectionner une clé de signature pour chaque fichier non signé ou modifié.|  
|**À propos de**|**Aide**||Affiche la version et les informations de copyright concernant MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Boîte de dialogue Préférences  
 La boîte de dialogue **Préférences** contient les éléments suivants.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Signer à l’enregistrement**|Vous invite à signer un fichier chaque fois que vous enregistrez vos modifications.|  
|**Utiliser le certificat de signature par défaut**|Utilise la clé entrée dans la zone de texte **Fichier de certificat** pour signer tous les fichiers. L’invite de signature qui apparaît généralement lorsque vous enregistrez un fichier ne s’affiche plus et **Signer à l’enregistrement** est sélectionné. Utilisez le bouton de sélection (**…**) en regard de la zone de texte **Fichier de certificat** pour sélectionner un fichier de clé.|  
|Algorithme de condensat|Définit l'algorithme avec lequel générer des compactés de dépendance. La valeur doit être « sha256RSA » ou « sha1RSA ». Utilise SHA1 comme valeur par défaut. Utilisée à la fois par les manifestes d'application et de déploiement. Si l'utilisateur fournit un certificat en enregistrant le manifeste, les algorithmes du certificat sont utilisés pour générer des condensés de dépendance.|  
  
## <a name="signing-options-dialog-box"></a>Boîte de dialogue Options de signature  
 La boîte de dialogue **Options de signature** apparaît lorsque vous enregistrez pour la première fois un manifeste ou une licence de confiance, ou lorsque vous modifiez ces derniers. Elle s’affiche uniquement si l’option **Signer à l’enregistrement** de la boîte de dialogue **Préférences** est sélectionnée. Vous devez être connecté à Internet lors de la signature d’un manifeste qui spécifie une valeur dans la zone de texte **URI du service d’horodatage**.  
  
 Cette boîte de dialogue contient les éléments suivants.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Signer avec le fichier de certificat**|Signe le manifeste avec un certificat numérique stocké dans le système de fichiers.|  
|**File**|Fournit une zone pour taper le chemin d’accès au fichier .pfx qui représente le certificat.|  
|**...**|Ouvre une boîte de dialogue **Choisir un fichier** pour sélectionner un fichier .pfx existant.|  
|**Nouveau**|Génère un nouveau fichier .pfx qui ne peut pas être vérifié par une Autorité de certification. Pour plus d’informations sur les types de certificats utilisés pour signer les déploiements ClickOnce, consultez [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Mot de passe**|Fournit une zone dans laquelle entrer le mot de passe utilisé pour signer ce certificat. Le cas échéant, peut être vide.|  
|**Signer avec le certificat stocké**|Affiche une liste dans laquelle sélectionner des certificats numériques stockés dans le magasin de certificats de votre ordinateur.|  
|**URI d’horodatage**|Affiche l'URI (Uniform Resource Identifier) d'un service d'horodatage numérique. Horodater les manifestes vous évite d'avoir à signer de nouveau les manifestes si votre certificat numérique expire avant le déploiement de la version suivante de votre application. Pour plus d’informations, consultez [Configurer des racines de confiance et des certificats non autorisés](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) et [ClickOnce et Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Ne pas signer**|Vous permet d'enregistrer le manifeste sans ajouter une signature d'un certificat numérique.|  
  
## <a name="tab-and-panel-descriptions"></a>Descriptions des onglets et des volets  
 Lorsque vous ouvrez un document avec MageUI.exe, il apparaît dans sa propre page d'onglets. Chaque onglet contient un ensemble de volets de propriétés. Les volets contiennent des sous-ensembles groupés des données du document.  
  
### <a name="application-manifest-tab"></a>Onglet Manifeste d'application  
 L’onglet **Manifeste d’application** affiche le contenu d’un manifeste d’application. Le manifeste d'application décrit tous les fichiers inclus dans le déploiement et les autorisations requises pour que l'application s'exécute sur le client.  
  
 L’onglet **Manifeste d’application** contient les onglets suivants.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Nom**|Spécifie les informations d'identification sur ce déploiement.|  
|**Description**|Spécifie des informations sur l'éditeur, le produit et la prise en charge.|  
|**Options de l’application**|Indique s'il s'agit d'une application de navigateur et si ce manifeste est la source des données de confiance.|  
|**Fichiers**|Spécifie tous les fichiers qui constituent ce déploiement.|  
|**Autorisations requises**|Spécifie le jeu d'autorisations minimum requis par l'application pour s'exécuter sur un client.|  
  
### <a name="name-tab"></a>Onglet Nom  
 L’onglet **Nom** s’affiche quand vous créez ou ouvrez un manifeste d’application pour la première fois. Il identifie de façon unique le déploiement et spécifie éventuellement une plateforme cible valide.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Nom**|Obligatoire. Nom du manifeste d'application. Généralement identique au nom de fichier.|  
|**Version**|Obligatoire. Numéro de version du déploiement sous la forme *N.N.N.N*. Seul le premier numéro de build majeur est obligatoire. Par exemple, pour la version 1.0 d’une application, les valeurs valides incluent `1`, `1.0`, `1.0.0` et `1.0.0.0`.|  
|**Processeur**|Optionnel. Architecture d'ordinateur sur laquelle ce déploiement peut s'exécuter. La valeur par défaut est `msil` (Microsoft Intermediate Language), ce qui correspond au format par défaut de tous les assemblys managés. Modifiez ce champ si vous avez précompilé les assemblys dans votre application pour une architecture spécifique. Pour plus d’informations sur la précompilation, consultez [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|  
|**Culturel**|Optionnel. Code pays et région ISO en deux parties dans lequel cette application s'exécute. La valeur par défaut est `neutral`.|  
|**Jeton de clé publique**|Optionnel. Clé publique utilisée pour signer ce manifeste d'application. S’il s’agit d’un manifeste nouveau ou non signé, ce champ affiche `Unsigned`.|  
  
### <a name="description-tab"></a>Onglet Description  
 Ces informations sont habituellement fournies dans le manifeste de déploiement. Ces champs peuvent uniquement être modifiés si la case **Utiliser les informations d’approbation du manifeste de l’application** est cochée sous l’onglet **Options d’application**.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Publisher**|Nom de la personne ou de l'organisation responsable de l'application. Cette valeur est utilisée comme nom de dossier du menu Démarrer.|  
|**Produit**|Nom complet du produit. Si vous avez sélectionné **Installation locale** pour l’élément **Type d’application** sous l’onglet **Options de déploiement** du manifeste de déploiement, ce nom apparaîtra dans le lien du menu **Démarrer** et dans **Ajout/Suppression de programmes** pour cette application.|  
|**Emplacement du support**|URL à partir de laquelle les clients peuvent obtenir de l'aide pour l'application.|  
  
### <a name="application-options-tab"></a>Onglet Options des applications  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Application de navigateur Windows Presentation Foundation**|Spécifie s'il s'agit d'une application WPF qui s'exécute dans le navigateur comme une application de navigateur XAML (XBAP).|  
|**Utiliser les informations d’approbation du manifeste de l’application**|Spécifie si ce manifeste contient des informations d'approbation.|  
  
### <a name="files-tab"></a>Onglet Fichiers  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Répertoire de l’application**|Répertoire dans lequel résident les fichiers de l'application. Utilisez le bouton de sélection (**…**) pour sélectionner le répertoire.|  
|**Remplir**|Ajoute tous les fichiers dans le répertoire de l'application et les sous-répertoires au manifeste de l'application. Si MageUI.exe trouve un seul fichier exécutable dans le répertoire, celui-ci est automatiquement marqué comme étant le point d'entrée, à savoir le fichier exécuté en premier quand l'application ClickOnce est lancée sur le client.|  
|**Fichiers de l'application**|Répertorie tous les fichiers dans l'application. Chaque fichier possède trois attributs modifiables, présentés ci-dessous.|  
|**Type de fichier**|Le type de fichier peut correspondre à l'une des quatre valeurs suivantes :<br /><br /> - Aucun.<br />- Point d’entrée. Fichier exécutable principal de l'application. Un seul fichier exécutable peut être marqué comme point d'entrée.<br />- Fichier de données. Fichier, tel qu'un fichier XML, qui fournit des données à l'application.<br />- Fichier icône. Icône d'application, comme celle qui apparaît sur le Bureau ou dans le coin de la fenêtre de l'application.|  
|**Facultatif**|Les fichiers marqués comme étant facultatifs ne sont pas téléchargées sur l'installation initiale ou une mise à jour, mais ils peuvent être téléchargés au moment de l'exécution à l'aide de l'API à la demande System.Deployment. Pour plus d’informations, consultez [Procédure pas à pas : téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce à l’aide du concepteur](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Groupe**|Étiquette d'un jeu de fichiers facultatifs. Vous pouvez appliquer une étiquette de groupe à un jeu de fichiers et utiliser l'API à la demande pour télécharger un lot de fichiers en un seul appel d'API.|  
  
### <a name="permissions-required-tab"></a>Onglet Autorisations requises  
 Utilisez l’onglet **Autorisations requises** si vous devez accorder à votre application un accès plus important à l’ordinateur local que celui accordé par défaut. Pour plus d’informations, consultez [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Type d’ensemble d’autorisations**|Spécifie le jeu d'autorisations minimum requis par l'application pour s'exécuter sur un client. Pour obtenir une description des jeux d’autorisations et des autorisations qu’ils exigent ou non, consultez [Jeux d’autorisations nommés](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Détails**|Code XML créé pour le manifeste d'application pour représenter le jeu d'autorisations. À moins d'avoir une bonne compréhension du manifeste d'application au format XML, vous ne devez pas modifier ce code XML manuellement. Pour plus d’informations, consultez [manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Onglet Manifeste de déploiement  
 L’onglet **Manifeste de déploiement** contient les onglets suivants.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Nom**|Spécifie les informations d'identification sur ce déploiement.|  
|**Description**|Spécifie des informations sur l'éditeur, le produit et la prise en charge.|  
|**Options de déploiement**|Spécifie des informations supplémentaires sur le déploiement, telles que le type d'application et l'emplacement de départ.|  
|**Options de mise à jour**|Spécifie à quelle fréquence ClickOnce doit vérifier les mises à jour de l’application.|  
|**Référence de l’application**|Spécifie le manifeste d'application pour ce déploiement.|  
  
### <a name="name-tab"></a>Onglet Nom  
 L’onglet **Nom** s’affiche quand vous créez ou ouvrez un manifeste de déploiement pour la première fois. Il identifie de façon unique le déploiement et spécifie éventuellement une plateforme cible valide.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Nom**|Obligatoire. Nom du manifeste de déploiement. Généralement identique au nom de fichier.|  
|**Version**|Obligatoire. Numéro de version du déploiement sous la forme *N.N.N.N*. Seul le premier numéro de build majeur est obligatoire. Par exemple, pour la version 1.0 d’une application, les valeurs valides incluent `1`, `1.0`, `1.0.0` et `1.0.0.0`.|  
|**Processeur**|Optionnel. Architecture d'ordinateur sur laquelle ce déploiement peut s'exécuter. La valeur par défaut est `msil` (Microsoft Intermediate Language), ce qui correspond au format par défaut de tous les assemblys managés. Modifiez ce champ si vous avez compilé les assemblys dans votre application pour une architecture spécifique.|  
|**Culturel**|Optionnel. Code pays/région ISO en deux parties dans lequel cette application s'exécute. La valeur par défaut est `neutral`.|  
|**Jeton de clé publique**|Optionnel. Clé publique utilisée pour signer ce manifeste de déploiement. S’il s’agit d’un manifeste nouveau ou non signé, ce champ affiche `Unsigned`.|  
  
### <a name="description-tab"></a>Onglet Description  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Publisher**|Obligatoire. Nom de la personne ou de l'organisation responsable de l'application. Cette valeur est utilisée comme nom de dossier du menu Démarrer.|  
|**Produit**|Obligatoire. Nom complet du produit. Si vous avez sélectionné **Installation locale** pour l’élément **Type d’application** sous l’onglet **Options de déploiement**, ce nom apparaîtra dans le lien du menu **Démarrer** et dans **Ajout/Suppression de programmes** pour cette application.|  
|**Emplacement du support**|Optionnel. URL à partir de laquelle les clients peuvent obtenir de l'aide pour l'application.|  
  
### <a name="deployment-options-tab"></a>Onglet Options de déploiement  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Type d’application**|Optionnel. Spécifie si cette application s’installe sur l’ordinateur client (**Installation locale**), s’exécute en ligne (**En ligne uniquement**) ou constitue une application WPF qui s’exécute dans le navigateur (**Application de navigateur WPF**). La valeur par défaut est **Installation locale**.|  
|**Emplacement de démarrage**|Optionnel. URL à partir de laquelle l'application doit réellement être démarrée. Utile lors du déploiement d'une application à partir d'un CD qui doit se mettre à jour lui-même à partir du web.|  
|**Inclure l’emplacement de démarrage (ProviderURL) dans le manifeste**|Optionnel. Spécifie l'URL vérifiée par ClickOnce pour les mises à jour d'application.|  
|**Exécuter automatiquement l’application après l’installation**|Obligatoire. Spécifie que l’application ClickOnce doit s’exécuter immédiatement après l’installation initiale à partir d’une URL. Par défaut, la case est cochée.|  
|**Autoriser la transmission des paramètres d’URL à l’application**|Obligatoire. Autorise le transfert de données de paramètre à l’application ClickOnce par le biais d’une chaîne de requête ajoutée à l’URL du manifeste de déploiement. Par défaut, la case est décochée.|  
|**Utiliser l’extension de fichier .deploy**|Obligatoire. Lorsque cette case est cochée, tous les fichiers du manifeste d'application doivent avoir l'extension .deploy. Par défaut, la case est décochée.|  
  
### <a name="update-options-tab"></a>Onglet Options de mise à jour  
 L’onglet **Options de mise à jour** contient uniquement les options mentionnées ici quand la zone de sélection **Type d’application** de l’onglet **Nom** affiche la valeur **Installation locale**.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Cette application doit vérifier les mises à jour**|Indique si ClickOnce doit vérifier les mises à jour de l’application. Si cette case n'est pas cochée, l'application ne vérifie pas les mises à jour, sauf si vous la mettez à jour par programme à l'aide des API de l'espace de noms <xref:System.Deployment.Application>.|  
|**Choisir à quel moment l’application doit rechercher les mises à jour**|Fournit deux options pour les vérifications des mises à jour :<br /><br /> -   **Avant le démarrage de l’application**. La vérification des mises à jour est effectuée avant l'exécution de l'application.<br />-   **Après le démarrage de l’application**. La vérification des mises à jour commence une fois que le formulaire principal de l'application s'est initialisé et s'exécutera au prochain démarrage de l'application.|  
|**Fréquence de vérification des mises à jour**|Détermine la fréquence à laquelle ClickOnce doit vérifier les mises à jour :<br /><br /> -   **Vérifier à chaque exécution de l’application**. ClickOnce effectue une vérification des mises à jour chaque fois que l’utilisateur ouvre l’application.<br />-   **Vérifier tou(te)s les **: sélectionnez un délai et une unité (heures, jours ou semaines) avant la vérification des mises à jour.|  
|**Spécifier une version minimale requise pour cette application**|Optionnel. Spécifie qu'une version spécifique de votre application est une installation obligatoire, pour empêcher les utilisateurs d'utiliser une version antérieure.|  
|**Version**|Obligatoire si la case **Spécifier une version minimale requise pour cette application** est cochée. Le numéro de version fourni doit être au format *N.N.N.N*. Seul le premier numéro de build majeur est obligatoire. Par exemple, pour la version 1.0 d’une application, les valeurs valides incluent `1`, `1.0`, `1.0.0` et `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Onglet Référence d'application  
 L’onglet **Référence d’application** contient les mêmes champs que l’onglet **Nom** décrit précédemment dans cette rubrique. La seule exception est le champ suivant.  
  
|Élément de l’interface utilisateur|Description|  
|----------------|-----------------|  
|**Sélectionner le manifeste**|Vous permet de choisir le manifeste d'application. Tous les autres champs de cette page se renseignent quand vous choisissez un manifeste d'application.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Procédure pas à pas : déploiement manuel d’une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Outil Manifest Generation and Editing)](mage-exe-manifest-generation-and-editing-tool.md)
