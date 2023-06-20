# G2P-UC2-ORS-S3-BookingDoctorsAppointment

<table data-header-hidden><thead><tr><th width="137"></th><th></th></tr></thead><tbody><tr><td>Use Case Step </td><td>     Booking a doctor’s appointment in the Health Application </td></tr><tr><td><p>Preconditions </p><p>(list of conditions that MUST be met in order to be able to successfully execute this process) </p></td><td><ul><li>The citizen has already registered/created an account in the health application portal.  </li><li>Good internet connectivity, access channels (web/mobile/kiosk) are available. </li><li>The citizen owns the identity proof (card, QR code, ID number, etc), mobile phone available together with the required credentials for the healthcare platform that can be verified and authenticated with the Health Application registry. </li></ul></td></tr><tr><td>Data inputs </td><td><ul><li>Username, Password </li><li>National ID number of the citizen </li><li>Electronic Health Record(EHR) number </li><li>Registered mobile number </li><li>Captcha Chat/non-robot verification </li><li>OTP </li></ul></td></tr><tr><td><p>Actors </p><p>(the people, organizations, computer systems - hardware and software, and building blocks that participate in the activity) </p></td><td><p>Human: Citizen </p><p>System:  </p><ul><li>Healthcare platform application </li><li>Digital Registries BB/(EHR) </li><li>Registration BB </li><li>Identity BB </li><li>Consent BB </li><li>Messaging BB </li><li>Information Mediator BB </li><li>National Population Registry (Digital Registries BB or Identity BB) </li><li>Scheduler BB </li><li>UI/UX BB </li></ul></td></tr><tr><td>Normal Course (what happens if the event is triggered and the preconditions have been met) </td><td><p>Once the user logs-in, the user should be able to search for list of hospitals, different services under each hospital, select the health service, upload documents (if necessary) and get a confirmation of the appointment. </p><p> </p><p>Step 1: The citizen  enters the required initial details, including, but not limited to the following: </p><ol start="1"><li>Username, password, Captcha, Mobile number, OTP </li></ol><ol start="2"><li> The application shall input the entered data, validate, and logs into the Health Application home page.  </li></ol><p>Feature: Verify and validate the citizen account details </p><p>Scenario: Healthcare Application retrieves citizen details from Health Application Registry.  </p><p>Given an Agreement citizen registration that exists in Consent BB </p><p>And Healthcare Application has Citizen’s &#x3C;Health Application Account ID> and authentication token for the registration session </p><p>When Healthcare application fetches a valid Health Application Account ID </p><p>Then Healthcare application successfully logs in the citizen </p><p></p><p>Step 2: The citizen searches for health care providers in a particular city </p><p>The Health Application introduces to the citizen a catalogue with filters/options consisting of cities, list of hospitals and clinics approved by the government. </p><p>The validated citizen ID/session ID fetches the details from &#x3C;Cities Registry>, and &#x3C;Hospitals Registry> with multiple filters. </p><p>Feature: Catalogue Search for identifying cities and healthcare providers </p><p> </p><p>Background: </p><p>Given Health Application/Session ID has the Application ID details associated with Citizen's ID and authentication token of the registration/log-in session  </p><p>Scenario: Search for Cities </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities </p><p>When Health application account ID/Session ID selects a city from the Cities Registry </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Cities Registry details are fetched successfully </p><p>Scenario: Search for Hospital/Clinic </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities </p><p>When Health application account ID/Session ID selects a city from the Cities Registry </p><p>And the &#x3C;Hospitals Registry> fetches all the hospitals and clinics under the selected cities </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital and Clinics details under  Cities Registry are fetched successfully </p><p></p><p>Step 3: The citizen views a catalogue of hospitals and clinics in the city and selects the department for which the appointment is required </p><p>The Health Application introduces to the citizen a catalogue with filters/options consisting of cities, list of hospitals and clinics approved by the government. </p><p>The validated citizen ID/session ID fetches the details from &#x3C;Departments Registry>, &#x3C;Services Registry>, with multiple filters; which are under &#x3C;hospitals registry> and &#x3C;cities registry>. </p><p>Feature: Catalogue Search for identifying departments and services (for example: Department of Neurology associated with Brain, Spine, Peripheral nerves, muscles related services etc.), with multiple filters. </p><p> </p><p>Background: </p><p>Given Health Application/Session ID has the Application ID details associated with Citizen's ID and authentication token of the registration/log-in session ; and has been presented with details of &#x3C;cities registry> and &#x3C;hospitals registry> </p><p> </p><p>Scenario: Search for Departments in a hospital </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals  </p><p>When Health application account ID/Session ID selects a hospital from the Hospitals Registry </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Departments Registry details are fetched successfully </p><p> </p><p>Scenario: Search for a service </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals, departments </p><p>When Health application account ID/Session ID selects a service from the Services Registry </p><p>And the &#x3C;Services Registry> fetches all the services under the Departments in a hospital in a city. </p><p> </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital, Clinics, Departments, Services details in a City are fetched successfully </p><p></p><p>Step 4: The citizen views available appointment slots in the calendar published by the particular hospital </p><p>The Health Application introduces to the citizen a catalogue with filters/options consisting of cities, list of hospitals and clinics approved by the government. The citizen selects a city, health provider, department and a service. </p><p>The validated citizen ID/session ID fetches the details from &#x3C;Cities Registry>, &#x3C;Departments Registry>, &#x3C;Hospitals Registry>, &#x3C;Services Registry>, with multiple filters. </p><p>Feature: Catalogue Search for appointment slot and its selection </p><p>Background: </p><p>Given Health Application/Session ID has the Health Application ID details associated with Citizen's ID and authentication token of the registration/log-in session  </p><p> </p><p>Scenario: Search for appointment slots in the catalogue </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals, departments </p><p>When Health application account ID/Session ID selects a service from the Services Registry </p><p>And the &#x3C;Services Registry> fetches all the services under the Departments in a hospital in a city </p><p>And a Catalogue of Appointment slots &#x3C;from Scheduler BB> are fetched successfully. </p><p> </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital, Clinics, Departments, Services, Scheduler BB time slots details in a City are fetched successfully </p><p> </p><p>Scenario: Citizen selects and confirms a slot. </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals, departments, services </p><p>When Health application account ID/Session ID selects a service from the Scheduler BBs catalogue/Time capability </p><p>And the &#x3C; Scheduler BB> fetches all the available slots for a service under the Departments in a hospital in a city </p><p>And a slot is selected, the details are communicated to Messaging BB successfully. </p><p> </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital, Clinics, Departments, Services, Appointment time slots details in a City are fetched successfully and the selected slot details are communicated to Scheduler BB, “Messaging BB” through IM BB. </p><p></p><p>Step 5: The citizen receives appointment details and the quote </p><p>The Health Application introduces to the citizen a catalogue with filters/options consisting of cities, list of hospitals, departments, services, appointment slots. </p><p>The validated citizen ID/session ID fetches the details from &#x3C;Cities Registry>, &#x3C;Departments Registry>, &#x3C;Hospitals Registry>, &#x3C;Services Registry>, with multiple filters. </p><p>Feature: The “Appointment” details are fetched from Scheduler BB and a quote (to submit additional information/time confirmation/pre-validation by citizen) is provided for citizen’s confirmation. </p><p> </p><p>Background: </p><p>Given Health Application/Session ID has the Application ID details associated with Citizen's ID and authentication token of the registration/log-in session  </p><p> </p><p>Scenario: Receive appointment details on Application UI/UX </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals, departments, services, appointment/time capability </p><p>When Health application account ID/Session ID selects a service time slot from the Scheduler BBs </p><p>And the &#x3C; Scheduler BBs > is selected; the details are communicated to Messaging BB successfully and then to UI/UX BB. </p><p> </p><p>Then IM BB fetches the payload from Messaging BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital, Clinics, Departments, Services, Appointment time slots details in a City are fetched successfully and the selected slot details from Scheduler BB are communicated to “Messaging BB” and then to UI/UX BB. </p><p></p><p>Step 6: The citizen accepts the quote and shares the medical information history required for the appointment </p><p>The citizen has been provided with appointment details, a quote to share additional but optional information. </p><p>Feature: The “Appointment” details are fetched and a quote (to submit additional information/time confirmation/pre-validation by citizen) is provided for citizen’s confirmation. </p><p> </p><p>Background: </p><p>Given Health Application/Session ID has the Application ID details associated with Citizen's ID and authentication token of the registration/log-in session  </p><p> </p><p>Scenario: Citizen shares additional details and then confirms the appointment. </p><p>Given Health application account ID/Session ID has been presented with catalogue of cities, hospitals, departments, services, appointment/time capability </p><p>When Health application account ID/Session ID selects a service from the Scheduler BBs catalogue of appointment slots. </p><p>And the &#x3C;Appointment slot in Scheduler BBs> is selected; the details are communicated to Messaging BB successfully and then to UI/UX BB for validation and to share/affix additional details. Citizen updates the details (optional) and confirms the appointment details. </p><p> </p><p>Then IM BB fetches the payload from Messaging BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Health application account ID/Session ID confirms to Health Application that Hospital, Clinics, Departments, Services, Appointment time slots details in a City are fetched successfully and the selected slot details are communicated to “Messaging BB” and then to UI/UX BB. The Registration BB is updated with new data (quotes) through Messaging BB and IM BB. Scheduler BB is updated. Appointment ID is updated in Health Application Account ID. The session is closed. </p><p></p><p>Step 7: The hospital staff validates the citizen’s appointment and consultation with the doctor  </p><p>The citizen has been provided with appointment details, a quote to share additional but optional information. The citizen confirms the appointment and receives the appointment details via paper or SMS. </p><p>Feature: Citizen visits the hospital on the scheduled time and the “Appointment”, received through a paper or SMS, is utilized. </p><p> </p><p>Background: </p><p>The hospital staff members cross checks the Appointment ID, Account ID, Citizen ID using UI/UX BB, Scheduler BB, Registration BB, Registries BB. </p><p> </p><p>Scenario: Citizen visits the hospital and hospital staff checks the appointment details </p><p> </p><p>Citizen shares the appointment details (Paper/SMS) with the hospital staff. The Staff logs-in to the portal and verifies and validates the appointment, citizen details. </p><p> </p><p>When Staff ID/Session ID selects an appointment ID from the  UI/UX, Scheduler BBs  </p><p>And the &#x3C; Appointment slot> is selected; the appointment and citizen details are communicated to IM BB and Scheduler BB and then to UI/UX BB for validation. Staff confirms the appointment details. </p><p> </p><p>Then IM BB fetches the payload from Scheduler BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Staff account ID/Session ID confirms to Staff Account that Citizen Health Application Account details, Hospital, Clinics, Departments, Services, Appointment time slots details in a City are fetched successfully and the selected slot details and citizen details are validated successfully.  </p><p></p><p>Step 8: The Hospital updates the prescriptions, diagnosis to the citizen in the Health Application </p><p>The citizen has visited the doctor and was advised some measures, medicines, diagnostics. The prescription and the in-house diagnostic services results are updated by the hospital staff in the patient registry associated with hospital account application ID of the citizen.  </p><p>Feature: The hospital staff uploads the prescriptions and diagnostics results of a citizen. </p><p> </p><p>Background: </p><p>Given Staff ID/Session ID has the Health Application Account ID associated with Citizen's ID and authentication token of the registration/log-in session  </p><p> </p><p>Scenario: Citizen shares the prescription with the staff after undergoing in-house diagnostic services with results. </p><p>Given Staff ID/Session ID has been presented with the Patients Registries </p><p>When Staff ID/Session ID selects a Hospital Account ID/Citizen ID </p><p>And the &#x3C; Patients Registry> is selected; the details are communicated to Messaging BB successfully and then to UI/UX BB. Staff updates/uploads the medicine advise/test result details (optional) associated with patients. </p><p> </p><p>Then IM BB fetches the payload from Registries BB (Does Dashboard &#x26; Analytics BB involves here? /Future use/scope?) </p><p>And Staff ID/Session ID confirms to Health Application that Health Account ID associated with Citizen ID are fetched successfully and the test results (optional) and prescriptions  are communicated to “IM BB” and then to UI/UX BB. The Registration BB is updated with new data (prescription/test results) through Messaging BB and IM BB. Patients Registry is updated. </p><p>In response, the Govstack IDBB/ Digital Registries BB is expected to return the following: </p><p> Data returned from Patients Registry </p></td></tr><tr><td><p>Alternative Course </p><p>(links to other use cases in case there are different ways how to solve the same use case) </p></td><td><p>If the Citizen does not possess a national ID, the registration application needs to provide an alternate mechanism for &#x3C;> </p><p>GetIdentityProfile – elaborate </p><p> </p><ol start="1"><li>If the consent record is previously created and available, the registration application should fetch the consent agreement by invoking the API: “serviceListIndividualRecord” on the Govstack Consent BB </li></ol><p>“GET /dataconsumer/consent/” </p></td></tr><tr><td>Data output </td><td><p>The successful completion of the citizen appointment process will result in confirmation and issuance of a Appointment ID that can be used by the citizen for future interactions with the hospital. </p><p> </p><p>Expected data from Registration BB </p></td></tr><tr><td>Post-Conditions (the success criteria) </td><td>The citizen has booked an appointment successfully in the Health Application. </td></tr><tr><td><p>Exceptions </p><p>(error situations) </p></td><td><ul><li>A citizen can book multiple appointments (but not at same time) in Health Application. The system must provision this. </li><li> Provide details on exception code and message </li></ul><ul><li>Mitigation steps: Describe steps to be taken by the actors </li><li> If the citizen has entered incorrect information then the Health Application inform the citizen to check/validate the same. </li></ul><ul><li>Provide details on exception code and message </li><li>Mitigation steps: Describe steps to be taken by the actors </li><li> If Identity BB or Consent BB is not available (service outage), then ….. </li></ul><ul><li>Mitigation steps: Describe steps to be taken by the actors </li><li> If no internet, then the system is not available and information must be collected on paper forms or on offline data capturing devices. </li></ul><ul><li>Mitigation steps: Describe steps to be taken by the actors </li></ul><p>If the citizen does not find a required department/services then either “general physician” or “This service is not available at this hospital” message shall be displayed. </p><p>If the appointment slots in a day are over the application and or Scheduler BB should make a suggestion such “There are no slots available for today” / “Please book your appointment on the next available day” </p></td></tr><tr><td><p>Related BBs </p><p>(working groups related to this example implementation) </p></td><td><ul><li>Identity BB </li><li>Consent BB </li><li>Registration BB </li><li>Digital Registries BB </li><li>Scheduler BB </li><li>Messaging BB </li><li>UI/UX BB </li></ul><p> </p></td></tr><tr><td>Sequence Diagram </td><td><p><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACEAAAAhCAYAAABX5MJvAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAZSURBVFhH7cEBAQAAAICQ/q/uCAIAAACgBhElAAGcWoyeAAAAAElFTkSuQmCC" alt="Shape blob:https://govstack-global.atlassian.net/3083b5b8-3512-4ffc-8414-12579334e565#media-blob-url=true&#x26;id=a0a8696e-e748-4408-b78f-e9a243b8740e&#x26;collection=contentId-112197720&#x26;contextId=112197720&#x26;height=1297&#x26;width=1200&#x26;alt="> </p><p>  </p></td></tr></tbody></table>