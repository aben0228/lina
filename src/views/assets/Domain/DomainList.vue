<template>
  <GenericListPage :table-config="tableConfig" :header-actions="headerActions" :help-message="notice" />
</template>

<script>
import { GenericListPage } from '@/layout/components'
import { DetailFormatter } from '@/components/ListTable/formatters/index'

export default {
  components: {
    GenericListPage
  },
  data() {
    return {
      tableConfig: {
        url: '/api/v1/assets/domains/',
        columns: [
          'name', 'asset_count', 'gateway_count', 'comment', 'actions'
        ],
        columnsMeta: {
          asset_count: {
            label: this.$t('assets.Assets')
          },
          gateway_count: {
            label: this.$t('assets.Gateway'),
            formatter: DetailFormatter,
            formatterArgs: {
              routeQuery: {
                activeTab: 'GatewayList'
              }
            }
          }
        }
      },
      headerActions: {
        hasBulkDelete: false,
        hasMoreActions: false,
        createRoute: 'DomainCreate'
      },
      notice: this.$t('assets.DomainHelpMessage')
    }
  }
}
</script>

<style>

</style>
