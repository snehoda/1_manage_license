# kompot_manage_license
manage license


import {baseEnvData} from "../../config/_base";
import {urlEndpoints, workersItems, workersHeaders} from "../../helper/names"
import {workersFlow1} from "../../helper/selectors";
import {verifyTextOfEl} from "../../helper/asserts";
import {clickOnEl, clickOnElByName, inputText, clickOnElByText, clickOnButton} from "../../helper/methods";


describe('Mange licenses for workers tests', () => {

    beforeEach('Login', () => {
        cy.apiLogin(baseEnvData.businessOwner.email, baseEnvData.businessOwner.password);
        cy.visit(urlEndpoints.workersEndpoint);
        clickOnElByName(workersFlow1.manageLicenses, workersItems.manageLicense)//opened new window
        cy.contains('Manage licenses').should('be.visible')
    });

    it.skip('Title Workers', () => {
        clickOnElByText(workersFlow1.titleWorkers, workersItems.workers)
    });

    it('Has text: "Manage worker licenses"', () => {
        // clickOnElByName(workersFlow1.manageLicenses, workersItems.manageLicense)//opened new window
        verifyTextOfEl(workersFlow1.manageWorkerLicenses, workersItems.manageLicenseNewWindow)
    });

    it('Close icon', () => {
        // clickOnElByName(workersFlow1.manageLicenses, workersItems.manageLicense)//opened new window
        clickOnEl(workersFlow1.closeIcon)
    })

    it('Has text "You can invite as many employees as you have licenses."', () => {
        verifyTextOfEl(workersFlow1.hasText, workersItems.manageLicenseText1)
    })

    it('Has text "Deactivated employees do not need a license."', () => {
        verifyTextOfEl(workersFlow1.hasText, workersItems.manageLicenseText2)
    })

    it('Has text "Purchased licenses"', () => {
        verifyTextOfEl(workersFlow1.hasText, workersItems.manageLicenseText3)
    })

    it('Has text "Active workers"', () => {
        verifyTextOfEl(workersFlow1.hasText, workersItems.manageLicenseText4)
    })

    it('Has text "Quantity"', () => {
        verifyTextOfEl(workersFlow1.quantityText, workersItems.quantityText)
    })

    it('Quantity field', () => {
        clickOnElByText(workersFlow1.quantityField, workersItems.quantityText)
        inputText(workersFlow1.quantityField, workersItems.quantityField)        // assert.typeOf('e2e', 'number', workersItems.quantity)
    })

    it.only('Buy License button"', () => {
        verifyTextOfEl(workersFlow1.buyLicenseButton, workersItems.buyLicenseButton)
        clickOnEl(workersFlow1.buyLicenseButton)
    })

})
