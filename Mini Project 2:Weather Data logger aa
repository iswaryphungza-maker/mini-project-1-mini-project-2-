#include <stdio.h>
#include <string.h>

/* Structure to store one weather record */
struct Weather {
    char datetime[50];     // Date & Time
    float temp;            // Temperature
    float humidity;        // Humidity
    float pressure;        // Pressure
};

int main(void) {

    struct Weather w;
    FILE *fp;
    int n, i;
    float sumT = 0, sumH = 0, sumP = 0;

    /* Open file in append mode (ASCII text) */
    fp = fopen("weather_log.txt", "a");

    printf("Enter number of readings: ");
    scanf("%d", &n);

    getchar();  // clear newline after scanf

    for (i = 0; i < n; i++) {

        printf("\nEnter Date & Time (DD-MM-YYYY HH:MM): ");
        fgets(w.datetime, sizeof(w.datetime), stdin);
        w.datetime[strcspn(w.datetime, "\n")] = '\0';  // remove newline

        printf("Enter Temperature: ");
        scanf("%f", &w.temp);

        printf("Enter Humidity: ");
        scanf("%f", &w.humidity);

        printf("Enter Pressure: ");
        scanf("%f", &w.pressure);

        getchar(); // clear newline before next fgets

        /* Write ASCII log to file */
        if (fp != NULL) {
            fprintf(fp, "%s  %.2f  %.2f  %.2f\n",
                    w.datetime, w.temp, w.humidity, w.pressure);
        }

        /* Show what was logged */
        printf("Logged: %s  %.2f  %.2f  %.2f\n",
               w.datetime, w.temp, w.humidity, w.pressure);

        /* Add for daily average */
        sumT += w.temp;
        sumH += w.humidity;
        sumP += w.pressure;
    }

    /* Print daily average */
    printf("\n--- DAILY AVERAGE ---\n");
    printf("Average Temperature = %.2f\n", sumT / n);
    printf("Average Humidity = %.2f\n", sumH / n);
    printf("Average Pressure = %.2f\n", sumP / n);

    if (fp != NULL) {
        fclose(fp);
    }

    return 0;
}
