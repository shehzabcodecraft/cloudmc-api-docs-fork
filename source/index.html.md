---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: curl
  - js

includes:
  - getting_started
  - administration
  # - administration/service_connections
  - administration/organizations
  - administration/users
  # - administration/roles
  - administration/additional_roles
  - administration/environments
  # - administration/resource_commitments
  - administration/usage
  # - administration/monetization
  # - administration/reports_pricing_v2 # Reporting section
  # - administration/notification_categories
  # - administration/notifications
  # - administration/products
  # - administration/pricings
  # - administration/applied_pricings
  # - administration/rollbacks
  # - administration/invoices
  # - administration/payments
  # - administration/package_discounts
  # - administration/organization_discounts
  # - administration/authentication
  # - administration/identity_providers
  # - administration/service_providers
  # - administration/saml_settings
  # - administration/branding
  # - administration/knowledge_base
  # - administration/trials
  # - administration/email_settings
  # - administration/feedback_settings
  # - administration/workspace_settings
  # - administration/custom_fields
  - administration/quotas
  - administration/activity_log
  # - administration/billing
  # - administration/billing_settings
  # - administration/billing_providers
  # - administration/tax_providers
  # - administration/custom_navigation
  # - administration/metrics
  # - administration/caches
  # - cloudstack
  # - cloudstack/compute # Compute section
  # - cloudstack/instances
  # - cloudstack/bare_metal_instances
  # - cloudstack/templates
  # - cloudstack/isos
  # - cloudstack/ssh_keys
  # - cloudstack/affinity_groups
  # - cloudstack/networking # Networking section
  # - cloudstack/vpcs
  # - cloudstack/networks
  # - cloudstack/network_acls
  # - cloudstack/public_ips
  # - cloudstack/port_forwarding_rules
  # - cloudstack/load_balancer_rules
  # - cloudstack/ingress_rules
  # - cloudstack/egress_rules
  # - cloudstack/nics
  # - cloudstack/remote_access_vpns
  # - cloudstack/vpn_users
  # - cloudstack/s2s_vpns
  # - cloudstack/storage # Storage section
  # - cloudstack/volumes
  # - cloudstack/snapshots
  # - cloudstack/offerings # Offerings section
  # - cloudstack/vpc_offerings
  # - cloudstack/network_offerings
  # - cloudstack/compute_offerings
  # - cloudstack/disk_offerings
  # - cloudstack/zones # Zones section
  # - openstack
  # - openstack/instances
  # - openstack/networks
  # - openstack/flavors
  # - openstack/images
  # - openstack/floatingIps
  # - openstack/securityGroups
  # - openstack/securityGroupRules
  # - openstack/routers
  # - openstack/routerInterfaces
  # - openstack/sshKeys
  # - openstack/volumes
  # - openstack/snapshots
  # - gcp
  # - gcp/compute # Compute section
  # - gcp/instances
  # - gcp/instance_groups
  # - gcp/disks
  # - gcp/ssh_keys
  # - gcp/health_checks
  # - gcp/snapshots
  # - gcp/networking # Networking section
  # - gcp/networks
  # - gcp/firewall_rules
  # - gcp/external_ips
  # - gcp/routes
  # - gcp/routers
  # - gcp/vpn_gateways
  # - gcp/vpn_tunnels
  # - gcp/subnets
  # - gcp/load_balancing # Load balancing subsection
  # - gcp/load_balancer
  # - gcp/forwarding_rules
  # - gcp/target_proxies
  # - gcp/backend_services
  # - gcp/ssl_certificates
  # - gcp/kubernetes # Kubernetes section
  # - gcp/clusters
  # - gcp/k8_namespaces
  # - gcp/k8_workloads
  # - gcp/k8_pods
  # - gcp/k8_deployments
  # - gcp/k8_daemonsets
  # - gcp/k8_statefulsets
  # - gcp/k8_networking
  # - gcp/k8_services
  # - gcp/k8_ingresses
  # - gcp/k8_ingresses_v1
  # - gcp/k8_configuration
  # - gcp/k8_configmaps
  # - gcp/k8_secrets
  # - gcp/k8_storage
  # - gcp/k8_storageclasses
  # - gcp/k8_persistentvolumes
  # - gcp/k8_persistentvolumeclaims
  # - gcp/k8_accesscontrol
  # - gcp/k8_serviceaccounts
  # - gcp/k8_roles
  # - gcp/k8_rolebindings
  # - gcp/k8_releases
  # - gcp/k8_charts
  # - gcp/images
  # - gcp/regions
  # - kubernetes
  # - kubernetes/k8_namespaces
  # - kubernetes/k8_workloads
  # - kubernetes/k8_pods
  # - kubernetes/k8_deployments
  # - kubernetes/k8_daemonsets
  # - kubernetes/k8_statefulsets
  # - kubernetes/k8_networking
  # - kubernetes/k8_services
  # - kubernetes/k8_ingresses
  # - kubernetes/k8_ingresses_v1
  # - kubernetes/k8_configuration
  # - kubernetes/k8_configmaps
  # - kubernetes/k8_secrets
  # - kubernetes/k8_storage
  # - kubernetes/k8_storageclasses
  # - kubernetes/k8_persistentvolumes
  # - kubernetes/k8_persistentvolumeclaims
  # - kubernetes/k8_accesscontrol
  # - kubernetes/k8_serviceaccounts
  # - kubernetes/k8_roles
  # - kubernetes/k8_rolebindings
  # - kubernetes/k8_releases
  # - kubernetes/k8_charts
  # - azure
  # - azure/compute
  # - azure/instances
  # - azure/regions
  # - azure/storage
  # - azure/disks
  # - azure/networking
  # - azure/networks
  # - azure/subnets
  # - azure/network_security_groups
  # - azure/security_rules
  # - azure/public_ip_addresses
  # - azure/kubernetes # Kubernetes section
  # - azure/clusters
  # - azure/k8_namespaces
  # - azure/k8_workloads
  # - azure/k8_pods
  # - azure/k8_deployments
  # - azure/k8_daemonsets
  # - azure/k8_statefulsets
  # - azure/k8_networking
  # - azure/k8_services
  # - azure/k8_ingresses
  # - azure/k8_ingresses_v1
  # - azure/k8_configuration
  # - azure/k8_configmaps
  # - azure/k8_secrets
  # - azure/k8_storage
  # - azure/k8_storageclasses
  # - azure/k8_persistentvolumes
  # - azure/k8_persistentvolumeclaims
  # - azure/k8_accesscontrol
  # - azure/k8_serviceaccounts
  # - azure/k8_roles
  # - azure/k8_rolebindings
  # - swift
  # - swift/containers
  # - swift/objects
  # - stackpath
  # - stackpath/edge_compute
  # - stackpath/workloads
  # - stackpath/instances
  # - stackpath/network_policy_rules
  # - stackpath/edge_delivery
  # - stackpath/sites
  # - stackpath/origin_settings
  # - stackpath/delivery_domains
  # - stackpath/cdn
  # - stackpath/waf
  # - stackpath/firewall_rules
  # - stackpath/scripts
  # - stackpath/edgessl
  # - stackpath/edgessl_settings
  # - stackpath/certificates
  # - stackpath/edgerules
  # - stackpath/predefined_edgerules
  # - stackpath/custom_rules
  # - stackpath/delivery_rules
  # - stackpath/images
  # - stackpath/dns_zones
  # - stackpath/dns_records
  # - aws
  # - aws/compute
  # - aws/instances
  # - aws/storage
  # - aws/volumes
  # - aws/s3
  # - aws/s3_api_credentials
  # - aws/buckets
  # - aws/objects
  # - aws/networking
  # - aws/vpcs
  # - aws/subnetworks
  # - aws/internetgateways
  # - aws/routes
  # - aws/availability_zones
  # - aws/elastic_ips
  # - aws/cidr_blocks
  # - aws/cidr_reservations
  # - purestorage
  # - purestorage/object_storage_api_credentials
  # - purestorage/buckets
  # - purestorage/objects
  - edge_compute
  - edgecompute/workloads
  - edgecompute/instances
  - edgecompute/network_policy_rules
  - edgecompute/images
  - edge_delivery
  - edgedelivery/sites
  - edgedelivery/origin_settings
  - edgedelivery/delivery_domains
  - edgedelivery/cdn
  - edgedelivery/waf
  - edgedelivery/firewall_rules
  - edgedelivery/scripts
  - edgedelivery/edgessl
  - edgedelivery/edgessl_settings
  - edgedelivery/certificates
  - edgedelivery/edgelogic
  - edgedelivery/predefined_edgelogic
  - edgedelivery/custom_rules
  - edgedelivery/delivery_rules

search: true
---
