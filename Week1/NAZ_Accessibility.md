# FACN4 Accessibility 02-07-18

1.  How to write an accessible navigation bar (navbar)

    There are number of techniques to use to write an accessible navigation bar:

    - **Allow Users to Skip Content** - You should give users the option to skip irrelevant or redundant content when possible. The most common way to do this is by adding a hidden ‘Skip to Content’ link in your header
    - **Add an Accessibility Menu** - Sites can go to extra lengths to create comprehensive accessibility menus accessed via the keyboard. These menus provide alternative navigations altogether to simplify an impaired or disabled individual’s experience
    - **Consider Keyboard Shortcuts**- Keyboard shortcuts offer an opportunity to let users navigate and perform many actions on your site with only a button. This significantly reduces the frustration for individuals with limited mobility or vision.
    - **Properly Structure and Label Elements** - Ensuring that all sections of your page are descriptively labeled as landmarks and your type hierarchy is correct will allow users to confidently skip entire irrelevant sections of your site to find the specific content that they are looking for.

2.  How to write an accessible modal
    - **What is a modal box?** - A modal box is a scripted effect that allows you to overlay a small element over a website.
    - **When are they used? -** There are 5 common use cases for modals:
      1.  Error: To alert users of an error.
      2.  Warning: To warn users of potentially harmful situations.
      3.  Data: To collect data from users.
      4.  Confirm or Prompt: To remind users to do something before moving on.
      5.  Helper: To inform users of important information.
    - **What are the benefits?** They avoid the need to use conventional pop-ups or page reloads. This leads to better usability as information is shown information quicker and in a more user friendly way
    - **What are the drawbacks** -
      - If coded incorrectly, modal boxes, like pop-up boxes, can have accessibility issues especially for users with screen readers
      - Why: A number of reasons but two main ones:
        1.  Providing context without visuals
        2.  Exiting the modal
    - **So how do you create an accessible modal box** -
      1.  Mark-up: Make sure the dialog box is marked up properly using Accessible Rich Internet Applications (ARIA) attributes such as aria-labelledby
      2.  Initial focus: Use the JS .focus() method to correct set the focus to the modal box
      3.  Exit: Make sure pressing Escape will close your dialog, and usually discard any changes.
      4.  After: On Dialog Close, Return Focus to Last Focused Element
      5.  No JS: Always have a solution that works even when JavaScript is disabled.

#
