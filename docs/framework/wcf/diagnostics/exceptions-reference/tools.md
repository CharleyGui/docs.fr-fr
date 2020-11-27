---
title: Outils
ms.date: 03/30/2017
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
ms.openlocfilehash: 2f7ef8b7f871dada676eb05713d6f624427d5395
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285692"
---
# <a name="tools"></a>Outils

Cette rubrique répertorie toutes les exceptions générées par les outils Windows Communication Foundation (WCF).

## <a name="exception-list"></a>Liste des exceptions

|Code de la ressource|Chaîne de la ressource|
|-------------------|---------------------|
|ParametersTarget|\<enum>|
|ParametersToolConfig|\<configFile>|
|ErrInvalidPath|Le chemin spécifié est incorrect. Vérifiez l’argument spécifié.|
|ParametersReference|\<file path>|
|WrnCannotLoadConfigFileForValidation|Une erreur s'est produite lors du traitement du fichier de configuration chargé depuis l'emplacement spécifié. Les services définis dans ce fichier de configuration ne peuvent pas être validés.|
|MoreHelp|Pour obtenir une assistance, tapez « svcutil » avec les arguments spécifiés.|
|HelpMergeConfig|Fait en sorte que la configuration générée soit fusionnée dans un fichier existant au lieu de remplacer le fichier existant.|
|ErrCannotWriteFile|Impossible d'écrire dans un fichier de sortie.|
|ErrInvalidNamespaceArgument|La valeur non valide spécifiée a été passée à l'option spécifiée. Spécifiez une paire d'espace de noms cible et d'espace de noms CLR séparés par des virgules.|
|HelpImportXmlType|Configure le sérialiseur DataContract de façon à importer des types non-DataContract comme types IXmlSerializable.|
|ErrExclusiveOptionsSpecified|L'option spécifiée ne peut pas être utilisée lorsque l'autre option spécifiée a été spécifiée.|
|WrnHttpGetFailed|Erreur GET HTTP avec l'URI spécifié.|
|ErrInputFileNotAssemblyOrMetadata|Le fichier à l'emplacement spécifié lu via l'argument d'entrée spécifié semble ne pas être un fichier de métadonnées XML ou un assembly valide.|
|WrnUnknownMetadataFound|Impossible d'enregistrer le document de métadonnées non reconnu du type spécifié.|
|ErrDirectoryContainsInvalidCharacters|La valeur non valide spécifiée a été passée à l'option spécifiée. Le caractère spécifié n'est pas autorisé dans un chemin d'accès.|
|WrnCannotResolveServiceForValidation|Impossible de charger un service avec le configName spécifié. Pour valider un service, fournissez à la fois l'assembly qui contient le type de service et un fichier exécutable avec la configuration pour ce service.|
|ErrUnexpectedValue|L'option spécifiée ne prend pas en charge de valeurs.|
|#InvalidArg|Le spécifié contient un argument non valide.|
|ParametersExcludeType|\<type>|
|HelpXmlSerializer|Générez des types de données qui utilisent le XmlSerializer pour la sérialisation et la désérialisation.|
|#|---------------------------------------------------------------------------------------------------------------------=|
|ErrUnexpectedError|Une erreur s'est produite dans l'outil.|
|HelpNologo|Le message de bannière et de copyright est supprimé.|
|ErrInputConflictsWithTarget|Le type d'entrée lu à partir du spécifié n'est pas pris en charge avec l'option spécifiée définie à la valeur spécifiée.|
|WrnCannotLoadServiceForExport|Une erreur s'est produite lors du chargement du type de service à exporter.|
|HelpMetadataDownloadCategory|- = TÉLÉCHARGEMENT DE MÉTADONNÉES = -|
|WrnNoServiceContractTypes|Impossible de générer des types XmlSerializer pour l'assembly spécifié. Aucun type de contrat de service n'a été trouvé.|
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Une erreur s'est produite lors du chargement des types dans un assembly qui a été chargé à partir du spécifié. Certains types dans l'assembly ne peuvent pas être chargés et sont inaccessibles à l'outil.|
|ErrDirectoryPointsToAFile|La valeur non valide spécifiée a été passée à l'option spécifiée. La valeur spécifiée est un chemin d’accès à un fichier.|
|Error|Erreur :|
|ErrDuplicateReferenceValues|L'assembly spécifié a été chargé deux fois à l'aide de l'option spécifiée. Un assembly ne peut être référencé qu'une seule fois.|
|WrnNoXmlSerializerOperationBehavior|Impossible de générer XmlSerializer pour l'assembly spécifié. Aucun contrat de service dans l'assembly n'a une opération avec XmlSerializerOperationBehavior.|
|ErrCannotCreateDirectory|Impossible de créer le répertoire spécifié.|
|ErrCouldNotLoadTypesFromAssemblyAt|Impossible de charger un type dans l'assembly spécifié.|
|ErrUnknownSwitch|Le commutateur spécifié est une option non reconnue.|
|Logo|Le logo de l'outil est « Microsoft ® Service Model Metadata Tool » avec la version.|
|NoCodeWasGenerated|Aucun code n'a été généré.<br /><br /> Si vous essayiez de générer un client, cette erreur peut être due au fait que les documents de métadonnées ne contenaient pas de contrats ou services valides<br /><br /> ou au fait que tous les contrats/services ont été découverts comme existant dans des assemblys de référence. Vérifiez que vous avez passé tous les documents de métadonnées à l'outil.|
|WrnUnableToLoadContractForSGen|Une erreur s'est produite lors du chargement d'un type de contrat. Impossible de générer le type XmlSerializer pour ce contrat. Le type et les détails sont spécifiés.|
|WrnOptionConflictsWithInput|L'option spécifiée ne peut pas être utilisée avec plusieurs assemblys d'entrée. L'option spécifiée est ignorée.|
|ErrUnableToImportMetadata|Une erreur critique s'est produite lors de la tentative d'importation des métadonnées.|
|ErrInvalidSerializer|Une valeur de sérialiseur non valide a été passée à l'option spécifiée. Les sérialiseurs pris en charge sont spécifiés.|
|SavingDownloadedMetadata|Enregistrement des fichiers de métadonnées téléchargés...|
|WrnNoConfigForServices|Aucun des assemblys passés n'était un exécutable avec fichier de configuration ou aucun des fichiers de configuration ne contenait des services avec le nom de configuration spécifié.|
|ErrInputConflictsWithOption|L'entrée lue à partir du spécifié ne peut pas être utilisée avec l'option spécifiée car elles impliquent différents modes d'opération de l'outil.|
|ErrUnableToExportEndpoints|Une erreur s'est produite lors de l'exportation du type de service spécifié.|
|ErrInputSchemaParseError|Une erreur d'analyse de schéma XML s'est produite lors de la lecture du spécifié. Vérifiez que le XML est correctement structuré et valide.|
|ErrInputPolicyParseError|Une erreur d'analyse WS-Policy s'est produite lors de la lecture du spécifié. Vérifiez que le XML est correctement structuré et valide.|
|ErrUnableToLoadReferenceType|Une erreur s'est produite lors du chargement d'un type de contrat référencé. Ce type spécifié est ignoré.|
|WrnCannotLoadServiceForValidation|Une erreur s'est produite lors du chargement du service à valider. Le type et les détails sont spécifiés.|
|HelpCodeGenerationCategory|-= GÉNÉRATION DE CODE =-|
|RetreivingMetadataWithMexAndDisco|Tentative de téléchargement de métadonnées à partir du spécifié à l'aide de WS-Metadata Exchange ou DISCO.|
|ErrGeneralSchemaValidation|Une erreur s'est produite lors de la vérification des schémas XML générés pendant l'exportation.|
|ParametersDirectory|\<directory>|
|ErrCannotLoadSpecifiedType|Aucun type ne peut être chargé pour la valeur spécifiée passée à l'option spécifiée. Assurez-vous que l'assembly auquel ce type appartient est spécifié à l'aide de l'option spécifiée.|
|ErrOptionModeConflict|L'option spécifiée ne peut pas être utilisée avec l'option spécifiée car elles impliquent des types de sortie différents.|
|ErrIsNotAnAssembly|Impossible de charger le spécifié en tant qu'assembly. Vérifiez que ce fichier est un assembly .NET.|
|ErrInputConflictsWithMode|L'entrée lue à partir du spécifié est incohérente avec d'autres options.|
|ErrDuplicateValuePassedToTypeArg|La valeur spécifiée a été passée plusieurs fois à l'option spécifiée. Chaque type ne peut être spécifié qu'une seule fois.|
|ErrInputEPRFileParseError|Impossible de lire la référence du point de terminaison à partir du spécifié. Vérifiez que le XML est correctement structuré et valide.|
|ErrCouldNotCreateCodeProvider|Impossible de créer un fournisseur de code pour la valeur spécifiée qui a été passée à l' {1} argument/. Vérifiez que le fournisseur de code est installé et configuré correctement.|
|ErrPathTooLongDirOnly|Le chemin d’accès spécifié résultant est trop long. Examinez l'argument spécifié.|
|HelpDataContractSerializer|Générez des types de données qui utilisent le sérialiseur DataContract pour la sérialisation et la désérialisation.|
|ErrUnableToExportEndpoint|Une erreur s'est produite lors de l'exportation du nom de point de terminaison spécifié dans l'espace de noms spécifié dans le type de service spécifié mentionné dans le fichier de configuration chargé pour l'assembly.|
|HelpUsage1|Affiche l'utilisation de l'aide.|
|HelpUsage2|Affiche l'utilisation de l'aide.|
|HelpUsage3|Affiche l'utilisation de l'aide.|
|HelpUsage4|Affiche l'utilisation de l'aide.|
|HelpUsage5|Affiche l'utilisation de l'aide.|
|ErrDirectoryNotFound|Le répertoire spécifié est introuvable. Vérifiez que le répertoire existe et que vous avez les autorisations appropriées pour le lire.|
|ErrUnableToLoadFile|Impossible de lire le fichier spécifié.|
|ErrNoFilesFound|Le chemin d’accès d’entrée spécifié semble ne faire référence à aucun fichier existant.|
|ParametersConfig|\<configFile>|
|ErrDirectoryInsteadOfFile|Le chemin d’accès d’entrée spécifié semble être un répertoire. L’entrée doit être un URL ou un chemin d’accès de fichier.|
|HelpConfig|Fait en sorte que les outils génèrent un fichier de configuration avec le nom fourni. Par défaut : output.config.|
|ErrSingleUseSwitch|L'option spécifiée ne peut pas être spécifiée à plusieurs reprises.|
|Avertissement|Avertissement :|
|WrnAmbiguousServiceConfig|Plusieurs configurations de service ont été détectées avec le nom de configuration spécifié, les assemblys suivants sont spécifiés.|
|ErrInvalidInputPath|Le chemin d’accès d’entrée spécifié semble ne faire référence à aucun fichier existant et ne semble pas être un URI valide.|
|ErrUnableToLoadInputs|Une erreur s'est produite lors de la lecture des métadonnées chargées.|
|GeneratingSerializer|Génération des sérialiseurs XML...|
|HelpToolConfig|Fichier de configuration personnalisé à utiliser à la place du fichier de configuration de l'application. Cela peut être utilisé pour modifier la configuration de métadonnées ou pour inscrire des extensions de configuration sans modifier le fichier de configuration de l'outil.|
|ErrValidateInvalidUse|L'option spécifiée ne peut pas être utilisée avec l'option spécifiée.|
|WrnWSMExFailed|Erreur WS-Metadata Exchange avec l'URI spécifié.|
|HelpNoconfig|Ne pas générer de configuration.|
|HelpCodeGenerationDescription|Le spécifié peut générer des contrats de service, des clients et des types de données à partir de documents de métadonnées.|
|HelpTargetMetadata|Métadonnées de sortie. Si l'entrée est une URL, Svcutil.exe enregistre les métadonnées sur disque et ne génère pas de code. Si l'entrée est un ou plusieurs assemblys, Svcutil.exe génère les métadonnées à partir des types dans les assemblys.|
|ErrAmbiguousOptionModeConflict|L'option spécifiée est en conflit avec d'autres options. Examinez votre utilisation de l'outil.|
|ErrNotLanguageOrCodeDomType|La valeur spécifiée passée à l’argument spécifié ne représente pas de langage défini et ne peut pas être chargée en tant que type CLR qualifié complet.|
|ErrUnableToUniquifyFilename|Impossible de créer le nom de fichier de sortie. Trop de fichiers sont créés avec le préfixe spécifié.|
|ErrCannotCreateFile|Impossible de créer le fichier de sortie spécifié.|
|ErrExpectedValue|L'option spécifiée requiert qu'une valeur soit spécifiée.|
|ErrCannotDisambiguateSpecifiedTypes|Il existe plusieurs types avec le même nom dans l'ensemble d'assemblys référencés. Utilisez des noms d'assemblys complets pour effectuer la distinction entre les types spécifiés pour l'option spécifiée.|
|RetreivingMetadataWithMexOnly|Tentative de téléchargement de métadonnées à partir de l'emplacement spécifié à l'aide de WS-Metadata Exchange. Cette URL ne prend pas en charge DISCO.|
|ErrInvalidTarget|La cible spécifiée n'est pas valide lorsqu'elle est spécifiée à l'aide de l'option spécifiée. Les cibles prises en charge sont spécifiées.|
|ErrPathTooLong|Le chemin d’accès résultant est trop long. Examinez les arguments spécifiés.|
|HelpCommonOptionsCategory|- = OPTIONS COURANTES = -|
|ParametersServiceName|\<serviceConfigName>|
|ErrNoValidInputFilesSpecified|Aucun fichier d'entrée valide n'a été spécifié. Spécifiez des documents de métadonnées ou des fichiers d'assembly.|
|ParametersLanguage|\<language>|
|ErrUnableToLoadMetadataDocument|Une erreur s'est produite lors de la lecture des métadonnées à partir de l'un des documents chargés. L'identificateur de document est spécifié.|
|ErrConflictingInputs|L’argument d’entrée spécifié est en conflit avec le spécifié car ils impliquent différents modes d’opération d’outil.|
|WrnUnableToLoadContractForValidation|Une erreur s'est produite lors du chargement d'un type de contrat. Le type et les détails sont spécifiés.|
|WrnAttributeReflectionErrors|La réflexion d'attribut a échoué pour certains des types dans l'assembly qui ont été chargés à partir du spécifié. Vérifiez que cet assembly peut être chargé à partir de cet emplacement avec les privilèges de sécurité corrects.|
|HelpMetadataExportCategory|- = EXPORT DE MÉTADONNÉES = -|
|HelpValidationCategory|- = VALIDATION DU SERVICE = -|
|ValidationError|Erreur de validation :|
|GeneratingFiles|Génération de fichiers…|
|ErrCannotSpecifyMultipleMappingsForNamespace|Une valeur non valide a été passée à l'option spécifiée. L'espace de noms cible spécifié ne peut pas être mappé à plusieurs espaces de noms CLR comme spécifié.|
|ErrCouldNotLoadReferenceAssemblyAt|Impossible de charger l'assembly de référence spécifié.|
|ParametersOut|\<file>|
|NoCodeWasGeneratedSuggestDCOnly|Pour générer des contrats à partir des schémas, utilisez l'option spécifiée.|
|ErrUnableToLoadInputConfig|Impossible de charger le fichier de configuration spécifié.|
|ErrUnexpectedDelimiter|Un séparateur d’arguments non valide (’:’ ou ’=’) ne peut pas démarrer l’option.|
|ErrMergeConfigUsedWithoutConfig|Impossible d'utiliser l'option spécifiée sans spécifier l'autre option spécifiée.|
|ErrUnableToExportContract|Une erreur s'est produite lors de l'exportation du contrat chargé à partir du type spécifié.|
|GeneratingMetadata|Génération de fichiers de métadonnées…|
|ErrNotCodeDomType|Le type spécifié qui é été passé à l'argument spécifié n'est pas de la classe dérivée spécifiée.|
|WrnNoTypeForServices|Aucun des assemblys passés ne contenait des types de service avec le nom de configuration spécifié.|
|ErrAssemblyLoadFailed|Impossible de charger le fichier spécifié en tant qu'assembly. Vérifiez les FusionLogs pour plus d'informations.|
|NoMetadataWasGenerated|Aucun fichier de métadonnées n'a été généré. Aucun contrat de service n'a été exporté.<br /><br /> Pour exporter un service, utilisez l'option spécifiée. Pour exporter des contrats de données, spécifiez l'option.|
|WrnCannotResolveServiceForExport|Impossible de charger un service avec le configName spécifié. Pour exporter un service, fournissez l'assembly qui contient le type de service et un fichier exécutable avec la configuration pour ce service.|
|ParametersCollectionType|\<type>|
|ErrOptionConflictsWithTarget|L'utilisation de l'option spécifiée n'est pas prise en charge avec l'option spécifiée définie à la valeur spécifiée.|
|ErrCodegenError|Une erreur s'est produite lors de la génération du code dans le langage spécifié.<br /><br /> Le langage ne prend pas en charge tous les éléments de code générés. Un autre langage doit être utilisé.|
|ErrInputWsdlParseError|Une erreur d'analyse WSDL s'est produite lors de la lecture du spécifié. Vérifiez que le XML est correctement structuré et valide.|
|ErrCouldNotCreateInstance|Impossible de créer une instance du type spécifié qui a été passé à l'argument spécifié.|
|ParametersNamespace|\<string,string>|
|HelpNostdlib|Ne faites pas référence à des bibliothèques standard (par défaut, mscorlib.dll et system.servicemodel.dll sont référencés.)|
|WrnCannotLoadConfigFileForExport|Une erreur s'est produite lors du traitement du fichier de configuration qui a été chargé à partir du spécifié. Les services définis dans ce fichier de configuration ne peuvent pas être chargés.|
|WrnUnableToLoadContractForExport|Une erreur s'est produite lors du chargement d'un type de contrat. Ce type spécifié ne peut pas être exporté.|
