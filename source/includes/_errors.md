# Errors

Django REST Framework has a standard way of returning error conditions in which the HTTP status code is the measure of success, and the JSON response body includes a single `"detail"` field with the cause of error. In the interest of not fighting the framework, most Roundware endpoints operate in the same manner. Errors will present a `HTTP 400 BAD REQUEST`, along with a detail field for explanation in most cases. Success will be in the form of a `HTTP 200`, along with a response body filled with relevant resulting data if any exists.
