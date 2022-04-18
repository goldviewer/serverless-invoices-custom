<template>
    <div>
        <strong class="break-line">
            <AppEditable :value="invoice.from_name"
                         :errors="errors"
                         field="from_name"
                         :placeholder="$t('your_company_name')"
                         @change="updateProp({ from_name: $event })"/>
            <i class="material-icons md-18 ml-2 pointer d-print-none" @click="editTeam">edit</i>
        </strong>

        <InvoiceTeamFields :invoice="invoice"/>

        <AppEditable :value="invoice.from_email"
                     :errors="errors"
                     field="from_email"
                     :placeholder="$t('your_email')"
                     @change="updateProp({ from_email: $event })"/>
    </div>
</template>
<script>
import AppError from '@/components/form/AppError';
import InvoiceTeamFields from '@/components/invoices/InvoiceTeamFields';
import AppEditable from '../form/AppEditable';

export default {
  i18nOptions: { namespaces: 'invoice-company-details' },
  props: ['invoice', 'errors'],
  components: {
    AppEditable,
    AppError,
    InvoiceTeamFields,
  },
  methods: {
    updateProp(props) {
      this.$emit('update', props);
    },
    editTeam() {
      this.$store.commit('teams/isModalOpen', true);
    },
  },
};
</script>
