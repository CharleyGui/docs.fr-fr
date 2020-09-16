---
title: Contrôle de l'enregistrement .NET Framework
description: Utilisez le suivi d’événements pour Windows (ETW) pour contrôler les événements de journalisation .NET et d’enregistrement common language runtime (CLR). Utilisez des outils tels que logman, Tracerpt et Xperf.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: bce5ea41149dc3b19106031fae202872dd8a8fb5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553803"
---
# <a name="controlling-net-framework-logging"></a>Contrôle de l'enregistrement .NET Framework

Vous pouvez utiliser le suivi d'événements pour Windows (ETW) pour enregistrer les événements du Common Language Runtime (CLR). Vous pouvez créer et afficher des traces à l'aide des outils suivants :

- Outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) qui sont inclus dans le système d’exploitation Windows.

- Outils en ligne de commande [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) du [Windows Performance Toolkit](/windows-hardware/test/wpt/). Pour plus d’informations sur Xperf, consultez le [blog des performances de Windows](/archive/blogs/pigscanfly/).

Pour capturer des informations sur les événements du CLR, le fournisseur du CLR doit être installé sur votre ordinateur. Pour confirmer que le fournisseur est bien installé, tapez `logman query providers` à l'invite de commandes. La liste des fournisseurs est affichée. Cette liste doit contenir une entrée pour le fournisseur du CLR, comme suit.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

Si le fournisseur du CLR n’apparaît pas dans la liste, vous pouvez l’installer sur Windows Vista et les systèmes d’exploitation ultérieurs à l’aide de l’outil en ligne de commande Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil). Ouvrez la fenêtre d’invite de commandes en tant qu’administrateur. Remplacez le répertoire de l’invite par le dossier .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4. \<.NET version> \ ). Ce dossier contient le fichier ETW.man du CLR. À l'invite de commandes, tapez la commande suivante pour installer le fournisseur du CLR.

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>Capture des événements ETW du CLR

Vous pouvez utiliser les outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour capturer des événements ETW, et les outils [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour décoder les événements Trace.

Pour activer la journalisation, un utilisateur doit spécifier trois éléments :

- Le fournisseur vers lequel communiquer.

- Un nombre 64 bits qui représente un jeu de mots clés. Chaque mot clé représente un jeu d'événements que le fournisseur peut activer. Le nombre représente un jeu combiné de mots clés à activer.

- Un petit nombre représentant le niveau (commentaires) à journaliser. Le niveau 1 est le moins détaillé, et le niveau 5 est le plus détaillé. Le niveau 0 est une valeur par défaut dont la signification est spécifique au fournisseur.

### <a name="to-capture-clr-etw-events-using-logman"></a>Pour capturer les événements ETW du CLR à l'aide de Logman

1. À l’invite de commandes, tapez :

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     où :

    - Le paramètre `-p` identifie le GUID du fournisseur.

    - `0x1CCBD` spécifie les catégories d'événements qui seront déclenchés.

    - `0x5` définit le niveau de la journalisation (dans ce cas, détaillé (5)).

    - Le paramètre `-ets` indique à Logman d'envoyer des commandes aux sessions de suivi d'événements.

    - Le paramètre `-ct perf` indique que la fonction `QueryPerformanceCounter` sera utilisée pour enregistrer l'horodatage de chaque événement.

2. Pour arrêter de journaliser les événements, tapez :

     `logman stop clrevents -ets`

     Cette commande crée un fichier de suivi binaire nommé clrevents.etl.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Pour capturer les événements ETW du CLR à l’aide de Xperf

1. À l’invite de commandes, tapez :

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     où le GUID est le GUID du fournisseur ETW du CLR et `0x1CCBD:5` effectue le suivi de tous les éléments de niveaux 5 (détaillé) et inférieurs.

2. Pour arrêter le suivi, tapez :

     `Xperf -stop clr`

     Cette commande crée un fichier de suivi nommé clrevents.etl.

## <a name="viewing-clr-etw-events"></a>Affichage des événements ETW du CLR

Utilisez les commandes répertoriées ci-dessous pour afficher les événements ETW du CLR. Pour obtenir une description des événements, consultez [Événements ETW du CLR](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Pour afficher les événements ETW du CLR à l'aide de Tracerpt

- À l’invite de commandes, tapez :

     `tracerpt clrevents.etl`

     Cette commande crée deux fichiers : dumpfile.xml et summary.txt. Le fichier dumpfile.xml répertorie tous les événements et le fichier summary.txt fournit un résumé des événements.

### <a name="to-view-clr-etw-events-using-xperf"></a>Pour afficher les événements ETW du CLR à l’aide de Xperf

- À l’invite de commandes, tapez :

     `xperf clrevents.etl`

     Cette commande ouvre la visionneuse de fichiers ETL de Xperf. Dans cette visionneuse, les événements CLR s’affichent dans la vue **Événements génériques**. Pour afficher une grille de données d’événements catégorisée par type, sélectionnez une plage horaire dans cette vue, puis cliquez avec le bouton droit et sélectionnez **Résumé**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Pour convertir le fichier .etl en fichier .csv

- À l’invite de commandes, tapez :

     `xperf -i clrevents.etl -f clrevents.csv`

     Cette commande indique à Xperf d’effectuer un dump des événements dans un fichier de valeurs séparées par des virgules (.csv) que vous pouvez consulter. Étant donné que des événements différents ont des champs différents, ce fichier .csv contient plusieurs lignes d'en-têtes avant les données. Le premier champ de chaque ligne correspond au type d'événement, qui indique l'en-tête à utiliser pour déterminer le reste des champs.

## <a name="see-also"></a>Voir aussi

- [Windows Performance Toolkit](/windows-hardware/test/wpt/)
- [Événements ETW dans le Common Language Runtime](etw-events-in-the-common-language-runtime.md)
