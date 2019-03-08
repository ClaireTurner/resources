---

copyright:

  years: 2017, 2019

lastupdated: "2019-02-19"

keywords: migrate, migrating to a resource group, migrate Cloud Foundry

subcollection: resources

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:gif: data-image-type='gif'}
{:tip: .tip}

# Migración de instancias de servicio y apps de Cloud Foundry a un grupo de recursos
{: #migrate}

Para hacer su experiencia con el uso de {{site.data.keyword.Bluemix}} más simple y flexible, hemos introducido [grupos de recursos](/docs/resources?topic=resources-rgs), que son conceptualmente similares a los espacios de Cloud Foundry. Sin embargo, los grupos de recursos incluyen varios beneficios adicionales, como el control de acceso más granular (mejor estructurado) utilizando IBM Cloud Identity and Access Management (IAM), la capacidad de conectar instancias de servicio a apps y servicios entre distintas regiones, y una forma sencilla de ver el uso por grupo.
{:shortdesc}

Estamos empezando a trasladar servicios desde Cloud Foundry para beneficiarse de los grupos de recursos, lo que significa que cuando seleccione el icono ![Migrar esta instancia de servicio a un grupo de recursos](images/migrate.svg "Migrar esta instancia de servicio a un grupo de recursos") junto a uno de los servicios del panel de control, debe iniciar un plan de migración para las instancias de servicio o apps que ha creado mediante la [{{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/developer/appservice/dashboard) para trasladar desde la organización y el espacio actual de Cloud Foundry a un grupo de recursos. Hasta que un servicio de {{site.data.keyword.Bluemix_notm}} se traslade de utilizar organizaciones, espacios y roles de Cloud Foundry a utilizar IAM y grupos de recursos, no podrá migrar las instancias de servicios existentes de Cloud Foundry a un grupo de recursos.

Cuando migre instancias de servicio o apps de {{site.data.keyword.dev_console}} de Cloud Foundry existentes a un grupo de recursos, no podrá cambiar el grupo que haya seleccionado una vez la migración se haya completado. Por lo tanto, es esencial que planifique cómo desea organizar los recursos en la cuenta antes de migrar. Esto puede requerir que cree uno o varios grupos de recursos, si dispone de una cuenta facturable, antes de realizar la migración.

Puede intentar organizar sus recursos en grupos de recursos de la misma forma que se han organizado los recursos en los espacios de Cloud Foundry. Para obtener más información sobre cómo utilizar grupos de recursos, consulte [Mejores prácticas para la organización de recursos en grupos de recursos](/docs/resources?topic=resources-bp_resourcegroups).
{: tip}


## ¿Por qué migrar?
{: #why_migrate}

### Instancias de servicio de Cloud Foundry
{: #cf_instances}

Los servicios que ofrecen soporte al control de acceso y organización de Cloud IAM en grupos de recursos disponen de varios beneficios:

* Al utilizar el control de acceso granular (estructurado), puede establecer el acceso a instancias de servicio individuales o un grupo de recursos organizado en un grupo de recursos.
* Mediante los grupos de acceso y los grupos de recursos para organizar usuarios y recursos, establezca solo el número mínimo de políticas de acceso. Por ejemplo, si tiene un conjunto de desarrolladores a los que desea que tengan acceso a recursos para un entorno de desarrollo, puede organizar todos esos usuarios en un grupo de acceso de desarrolladores y, a continuación, añadir todos los recursos a los que necesitan acceder en un único grupo de recursos. A continuación, puede establecer una política única para el grupo de acceso para tener acceso a todos los recursos del grupo de recursos.
* Puede ver el uso por grupo de recursos de forma similar a la forma en la que puede ver el uso de las organizaciones de Cloud Foundry.
* Puede conectarse a apps y servicios en cualquier espacio de Cloud Foundry, lo que permite conexiones para apps y servicios de distintas regiones. Cuando realice la migración, la conexión se establecerá automáticamente convirtiendo su instancia de servicio de Cloud Foundry original en un alias y creando una instancia enlazada a un grupo de recursos de su elección. El gráfico siguiente muestra cómo funciona la conexión utilizando un alias.

![Enlace de una instancia de servicio a un espacio de Cloud Foundry para crear un alias](images/alias.svg "Enlace de una instancia de servicio a un espacio de Cloud Foundry para crear un alias")

### {{site.data.keyword.dev_console}} apps
{: #app_services}

Anteriormente, las apps de {{site.data.keyword.dev_console}} podían estar asociadas solo con instancias de servicio de Cloud Foundry. Ahora, si migra las apps a un grupo de recursos, puede asociar las apps con instancias de servicio que pertenecen a un grupo de recursos y que dan soporte al control de acceso de Cloud IAM.

## ¿Quién puede migrar?
{: #whocanmigrate}

### Acceso necesario para las instancias de servicio
{: #required_access_instances}

Los usuarios deben tener acceso específico para migrar instancias de servicio de Cloud Foundry a un grupo de recursos:

* El usuario debe tener el rol de desarrollador en el espacio de Cloud Foundry o el rol de gestor de la organización de Cloud Foundry en la organización a la que pertenece la instancia.
* El usuario debe tener al menos el rol de IAM Visor para gestionar el grupo de recursos al que se va a migrar la instancia.
* El usuario debe tener al menos el rol de IAM Editor en el servicio.

Para obtener más información sobre la asignación del acceso correcto, consulte [Acceso de Cloud Foundry](/docs/iam?topic=iam-cfaccess) y [Acceso de IAM](/docs/iam?topic=iam-userroles#platformrolestable1).

Para comprobar el acceso que tiene, pulse **Gestionar** &gt; **Acceso (IAM)** en la barra de menús de la consola y, a continuación, pulse **Usuarios**. Pulse el nombre y revise las **Políticas de acceso** de los roles IAM asignados y el **Acceso de Cloud Foundry** para ver a qué organizaciones tiene acceso y los roles de Cloud Foundry que tiene asignados.
{: tip}

### Acceso necesario para apps de {{site.data.keyword.dev_console}}
{: #required_access_apps}

Cualquier usuario que tenga acceso a una app de {{site.data.keyword.dev_console}} puede migrarla. Sin embargo, la migración de una app no migra servicios asociados con la app. Las instancias de servicio deben migrarse por separado.

## ¿Cómo funciona la migración?
{: #how}

### Migración de instancias de servicio
{: #migrate_instances}

Cuando migra una instancia de servicio desde un espacio y organización de Cloud Foundry a un grupo de recursos, se crea en el grupo de recursos una nueva instancia de servicio enlazada. La instancia original de la organización y el espacio de Cloud Foundry pasa a ser un [alias](/docs/resources?topic=resources-connect_app#what_is_alias). El alias se tendrá en cuenta en relación con la cuota de su organización, pero se le facturará por el uso de la instancia de servicio en el grupo de recurso.

![Migración de una instancia de servicio de Cloud Foundry a un grupo de recursos](images/migration.gif){: gif}

Las instancias de servicio se migran de una en una cuando se lo notifique en la lista de recursos el icono ![Migrar esta instancia de servicios a un grupo de recursos](images/migrate.svg "Migrar esta instancia de servicio a un grupo de recursos") asociado a su instancia de servicio de Cloud Foundry.

Antes de iniciar el proceso de migración, revise la documentación del servicio para ver si hay algún cambio adicional específico del servicio que puede hacer cuando migra su instancia de servicio a un grupo de recursos. Por ejemplo, es posible que necesite migrar datos de instancias antiguas a instancias nuevas o actualizar las credenciales utilizadas para su app si suprime el alias de Cloud Foundry. Las aplicaciones que realicen una llamada directa a la API de un servicio que se ha migrado necesitan actualizar la llamada a la API para utilizar una clave de API IAM o una señal de acceso.
{: tip}

1. Abra el menú **Más acciones**.
2. Seleccione **Migrar a un grupo de recursos** para empezar.
3. Seleccione un grupo de recursos.
4. Pulse **Migrar** y la instancia se migrará.
5. Como solo puede migrar una instancia a la vez, puede continuar migrando instancias elegibles cuando haya realizado la migración de la primera.

Cuando haya migrado una instancia correctamente, la verá en la sección Servicio de la lista de recursos. El alias permanece en la sección de Cloud Foundry del panel de control. Puede utilizar el ![Icono de enlace](images/link.svg "Icono de enlace que representa un alias") en la sección de Cloud Foundry de la lista de recursos para identificar los alias.

### Migración de apps de {{site.data.keyword.dev_console}}
{: #migrate_apps}

Las apps se migran de una en una al pulsar el icono ![Migrar esta instancia de servicio a un grupo de recursos](images/migrate.svg "Migrar esta instancia de servicio a un grupo de recursos") asociado con cada entrada de la vista Lista de apps.

1. Seleccione el icono de **Menú** ![Icono de Menú](../icons/icon_hamburger.svg) y seleccione el portal del desarrollador de su interés como Watson, Mobile o Web Apps, por ejemplo.
2. Seleccione **Apps**, que muestra las listas **Apps (Acción necesaria)** y **Apps (migradas)**.
3. Para cada entrada de la lista **Apps (Acción necesaria)**, pulse el icono **Migrar** ![Migrar esta instancia de servicio a un grupo de recursos](images/migrate.svg "Migrar esta instancia de servicio a un grupo de recursos").
4. Seleccione o cree un nuevo grupo de recursos.
5. Pulse **Migrar** y la app se migrará.
6. Confirme que la app ahora se muestra en la lista **Apps (migradas)**.
7. Como solo puede migrar una app a la vez, puede continuar migrando apps elegibles cuando haya realizado la migración de la primera.


## Pasos siguientes
{: #migrate_next_steps}

Después de migrar sus instancias de servicio de Cloud Foundry a un grupo de recursos, debe asegurarse de que los usuarios de la cuenta tienen el nivel de acceso requerido a los recursos de los grupos de recursos de la cuenta. También es posible que desee proporcionar acceso para gestionar el grupo de recursos, de modo que los usuarios pueden crear nuevas instancias de servicio en los grupos de recursos de la cuenta.

Para obtener más información sobre la asignación de acceso a recursos de los grupos de recursos, consulte [Asignación de acceso a los grupos de recursos y a los recursos dentro de los mismos](/docs/resources?topic=resources-bp_resourcegroups#assigning_access_rgs).

Además, asegúrese de revisar la documentación para el servicio para ver si se debe realizar alguna actualización para las apps existentes una vez que se complete la migración.


## Resolución de problemas
{: #ts_migration}

Si se le presentan problemas al migrar instancias de servicio de Cloud Foundry, consulte [Resolución de problemas para servicios y recursos](/docs/resources?topic=resources-services).
