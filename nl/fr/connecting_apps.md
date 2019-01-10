---

copyright:
  years: 2017, 2018
lastupdated: "2018-10-29"

---

{:shortdesc: .shortdesc}

# Gestion des connexions
{: #connect_app}

Vous pouvez connecter un service à une application {{site.data.keyword.Bluemix}} nouvelle ou existants depuis l'onglet **Connexions** du tableau de bord de votre service. La connexion d'un service à une application crée une liaison entre ces deux éléments. Vous pouvez les dissocier, ajouter des connexions supplémentaires ou supprimer des connexions depuis l'onglet **Connexions**.

Toutefois, lorsque vous connectez une instance de service gérée par IAM ({{site.data.keyword.Bluemix_notm}} Identity and Access Management) à une application, un alias du service géré par IAM est automatiquement créé dans l'espace correspondant avec les informations de liaison que vous avez fournies. Cet alias est représenté comme une instance de service de votre service géré par IAM.
{:shortdesc}

## Qu'est-ce qu'un alias ?
{: #what_is_alias}

Un alias est une connexion entre votre service géré par IAM dans un groupe de ressources et une application dans une organisation ou un espace. Dans la console {{site.data.keyword.Bluemix_notm}}, la connexion (alias) est représentée comme une instance de service. Vous pouvez gérer votre alias en modifiant l'instance de service qui représente votre connexion.

Les alias sont comme des liens symboliques qui contiennent des références à des ressources distantes et qui activent l'interopérabilité et la réutilisation d'une instance sur l'ensemble de la plateforme. Par exemple, vous pouvez créer une instance d'un service dans un groupe de ressources, puis la réutiliser à partir de n'importe quelle région disponible en créant un alias dans une organisation ou un espace de ces régions.

Les règles suivantes s'appliquent aux alias :

* Un alias ne génère pas de coût supplémentaire, mais chaque alias est décompté de votre quota dans votre organisation.
* Vous ne pouvez créer qu'un seul alias par espace dans la console {{site.data.keyword.Bluemix_notm}}. Mais vous pouvez cependant créer plusieurs alias par espace à l'aide de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}. Pour plus d'informations, voir [Utilisation de ressources et de groupes de ressources](/docs/cli/reference/ibmcloud/cli_resource_group.html#ibmcloud_commands_resource).
* Vous pouvez créer plusieurs connexions entre votre service géré par IAM et toute application de n'importe quel espace, organisation et région dans le même compte si vous disposez du droit requis
* Toutes les connexions établies dans le même espace vers différentes applications à partir d'une instance de service gérée par IAM utilisent le même alias.
* La suppression de la liaison d'une instance de service gérée par IAM *ne supprime pas* l'instance de service qui représente l'alias.
* La suppression de l'application à laquelle votre instance de service gérée par IAM est connectée *ne supprime pas* l'instance qui représente l'alias.
* La suppression d'une instance de service gérée par IAM *supprime* l'instance de service qui représente l'alias.

## Création d'une connexion (alias) entre un service géré par IAM et une application
{: #creating_alias}

Pour connecter votre instance de service gérée par IAM à une application :

1. Accédez à votre tableau de bord.

2. Cliquez sur le nom de votre application pour ouvrir la vue des détails d'application.

3. Cliquez sur **Connecter un existant**, puis sélectionnez votre application existante. Ou cliquez sur **Créer une connexion** pour créer une application à laquelle se connecter.

4. Spécifiez le **Rôle d'accès pour la connexion**. Cette valeur définit le rôle d'accès du service IAM. Pour plus d'informations, voir [Accès IAM](/docs/iam/users_roles.html#userroles).

5. Facultatif : vous pouvez renseigner la zone **ID de service pour la connexion** soit en autorisant IAM à générer automatiquement une valeur unique, soit en fournissant l'ID d'un service existant. Pour plus d'informations, voir [Création et utilisation des ID de service](/docs/iam/serviceid.html#serviceids).

6. Cliquez sur **Créer**.

## Affichage d'un alias

Une fois que vous avez créé une connexion entre un service géré par IAM et une application, l'alias est affiché dans l'onglet **Connexions** de l'application connectée. De plus, l'alias est affiché en tant qu'instance de service en cours d'exécution sur votre liste de ressources et contient uniquement un onglet **Connexions** lorsque vous l'ouvrez.

1. Accédez à la liste de vos ressources.
2. Dans la table **Services d'application**, cliquez sur le nom de l'instance de service afin d'ouvrir la vue détaillée du service. Si elle ne contient qu'un onglet **Connexions**, il s'agit d'un alias.

## Suppression d'un alias

La manière la plus simple de supprimer un alias est de supprimer l'instance de service gérée par IAM. Vous pouvez toutefois conserver l'instance de service gérée par IAM et supprimer directement l'alias.

1. Accédez à la liste de vos ressources.
2. Dans la table **Services d'application**, cliquez sur le nom de l'instance de service afin d'ouvrir la vue détaillée du service. Si elle ne contient qu'un onglet **Connexions**, il s'agit d'un alias.
3. Supprimez l'instance.

## Création d'une connexion entre plusieurs services
{: #cf}

Pour plus d'informations, voir [Utilisation des services dans un autre service](/docs/resources/s2s.html#s2s_binding).
