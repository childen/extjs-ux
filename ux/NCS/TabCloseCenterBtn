/*
 * Erlaubt es Tabs in einem TabPanel mit der mittleren Maustaste zu schließen
 * Es werden nur Tabs geschlossen die "closable" sind
 */

Ext.define('Ext.ux.NCS.TabCloseCenterBtn', {
    alias: 'plugin.ncs_tabclosecenterbtn',
    mixins: {
        observable: 'Ext.util.Observable'
    },
    constructor: function(config) {
        this.mixins.observable.constructor.call(this, config);
    },
    init: function(cmp) {
        this.tabPanel = cmp;
        this.tabBar = cmp.down('tabbar');
        this.mon(this.tabPanel, {
            scope: this,
            afterlayout: this.onAfterLayout,
            single: true
        });
    },
    onAfterLayout: function() {
        this.mon(this.tabBar.el, {
            scope: this,
            click: this.onClickHandler,
            delegate: '.x-tab'
        });
    },
    onClickHandler: function(event, target) {
        var me = this;
        if (event.type === 'click' && event.button === 1) {
            var tab = me.tabBar.getChildByElement(target);
            var index = me.tabBar.items.indexOf(tab);
            me.item = me.tabPanel.getComponent(index);
            if (me.item.closable) {
                this.tabPanel.remove(me.item);
            }

        }
    }
});
