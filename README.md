## Refactoring

From [my PA4 code](https://github.com/OOP2020/PA4-Bheem6005)

In `src/FlashGet.java`

at `downloadHandle(ActionEvent e)` method:

Showing alert dialog is not downloadHandle work

Before refactoring:
```
    private void downloadHandle(ActionEvent e) {
        ...
        } catch (IOException ex) {
            Alert alert = new Alert(Alert.AlertType.ERROR, "Error: Invalid URL");
            alert.show();
        } catch (RejectedExecutionException ex) {
            Alert alert = new Alert(Alert.AlertType.ERROR, "Error: Previous download is unfinished");
            alert.show();
        }
    }
```
Extract `alertDialog(String text)` method to show alert dialog

After refactoring:
```
    private void downloadHandle(ActionEvent e) {
        ...
        } catch (IOException ex) {
            alertDialog("Error: Invalid URL");
        } catch (RejectedExecutionException ex) {
            alertDialog("Error: Previous download is unfinished");
        }
    }

    /**
     * Show alert dialog
     */
    private void alertDialog(String text) {
        Alert alert = new Alert(Alert.AlertType.ERROR, text);
        alert.show();
    }
```