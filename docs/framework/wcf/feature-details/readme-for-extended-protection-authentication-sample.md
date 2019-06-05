---
title: ReadMe pour l'exemple d'authentification de protection étendue
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: cc60ee32efcbe1e6ac1ce620fa1c17504db5197f
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690579"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>ReadMe pour l'exemple d'authentification de protection étendue

La Protection étendue est une initiative de sécurité pour vous protéger contre les attaques (d’intercepteur MITM) man-in-the-middle, dans lequel un attaquant (le « man-in-the-middle ») intercepte les informations d’identification d’un client et les utilise pour accéder aux ressources sécurisées sur le serveur du client prévue.

Pour plus d’informations, consultez [la Protection étendue pour une vue d’ensemble de l’authentification](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).

> [!NOTE]
> Cet exemple fonctionne uniquement dans le cadre d'un hébergement sur IIS. Ile ne fonctionne pas sur Visual Studio Development Server car il ne prend pas en charge HTTPS.

## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Installez IIS sur l’ordinateur à partir d’Ajout/Suppression de programmes -> fonctionnalités de Windows.

2. Activer l’authentification Windows dans les fonctionnalités de Windows : Internet Information Services -> World Wide Web Services -> sécurité -> de l’authentification Windows.

3. Activez activation HTTP dans les fonctionnalités de Windows : Microsoft .NET Framework 3.5.1 -> Activation HTTP de Windows Communication Foundation.

4. Cet exemple requiert l'établissement par le client d'un canal sécurisé avec le serveur et nécessite la présence d'un certificat de serveur qui peut être installé à partir du gestionnaire des services IIS (Internet Information Services).

    1. Ouvrez le Gestionnaire des services Internet -> certificats de serveur (à partir de l’onglet de vue fonctionnalité).

    2. À des fins de test de cet exemple, vous pouvez créer un certificat auto-signé. (Si vous ne souhaitez pas qu'Internet Explorer vous informe que le certificat n'est pas sécurisé, vous pouvez l'installer dans la banque d'autorités racine approuvées de certificats).

5. Accédez au volet Actions pour le site web par défaut. Cliquez sur Modifier Site -> liaisons. Ajoutez HTTPS comme type s'il ne l'est pas encore, avec le numéro de port 443, et affectez le certificat SSL créé à l'étape précédente.

6. Générez le service. Un répertoire virtuel est alors créé dans IIS (à partir de l'action post-build spécifiée dans les propriétés de projet) et les fichiers dll, .svc et de configuration sont copiés comme requis pour l'hébergement d'un service sur le Web.

7. Ouvrez le gestionnaire des services IIS. Cliquez avec le bouton droit sur le répertoire virtuel (ExtendedProtection) que vous avez créé à l'étape précédente et sélectionnez Convertir en application.

8. Ouvrez le module Authentification dans le gestionnaire des services IIS de ce répertoire virtuel et activez l'authentification Windows.

9. Ouvrez les paramètres avancés de l'authentification Windows pour ce répertoire virtuel et définissez la valeur Requis, car, dans cet exemple, le paramètre ExtendedProtection correspondant est défini sur Toujours.

10. Vous pouvez tester le service en accédant à l'URL depuis une fenêtre de navigateur. Si vous souhaitez accéder à cette URL depuis plusieurs ordinateurs, assurez-vous que le pare-feu est ouvert pour l'ensemble des connexions HTTP et HTTPS entrantes.

11. Ouvrez le fichier de configuration de client et de fournir un nom d’ordinateur complet pour le \<client >- \<point de terminaison >-attribut d’adresse, en remplaçant \<nom_complet_ordinateur >.

12. Exécutez le client. Le client communique avec le service en établissant un canal sécurisé et en utilisant une protection étendue de manière discrète.
