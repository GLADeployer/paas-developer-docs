For terminology that is used within PaaS, refer to [Cloud Foundry’s glossary](http://docs.cloudfoundry.org/concepts/glossary.html).

## Tenant
We refer to someone who is using PaaS to host a government app as a tenant or tenant user, as opposed to an end user who is a person using the hosted app.

## Organisations
Cloud Foundry users are grouped by [organisations](http://docs.cloudfoundry.org/concepts/roles.html#orgs), or "orgs" for short. Orgs group together CF users for management and present a shared perimeter for services, domains and quotas. As a tenant, when your account is created, you will be given permissions to an org and a personal space.

To list available orgs:

``cf orgs``

Only orgs where you've been assigned an org-role or those which contain a space where you've been assigned a space-role will appear.

To see details about a specific org, including quotas, routing domains and which spaces it includes:

``cf org ORGNAME``

In order to work with spaces, you'll need to do this first:

``cf target -o ORGNAME``

## Spaces
Every application is scoped to a [space](http://docs.cloudfoundry.org/concepts/roles.html#spaces). Applications in the same space share a location for app development, deployment, and maintenance.

To create a space:

``cf create-space SPACENAME``

**Note:**  To create a space within a given org you must have the `OrgManager` role. You can check to see which users and managers for your org with:

``cf org-users ORGNAME``

## Target
The Cloud Foundry CLI keeps a global state of whatever [organisation](#organisations)+[space](#spaces) you're interacting with. This is known as the "target", and is set via:

``cf target -o ORGNAME -s SPACENAME``

## Buildpacks
All apps need to use a 'buildpack' specific to their language, which sets up dependencies for particular language stacks. There are standard buildpacks for most languages, and they will usually be auto-detected by CF.

Note that Government PaaS does not support custom buildpacks.

